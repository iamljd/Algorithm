```cpp
//在set中每个元素的值都唯一，依次插入1、3、1，set中最后一个值仍为3，s.size()=2，最后一个1插入无效
//系统能根据元素的值自动进行排序
//在set中查找是使用二分查找
#include<set>
set<int> s;
```
####
    s.begin();                  *s.begin()=s[s.begin()],返回迭代器,set容器的第一个元素
    s.end();　　　　            返回迭代器,s的最后一个元素的下标加一
    s.clear();   　　           删除set容器中的所有的元素
    s.empty(); 　　             返回bool值,判断set容器是否为空
    s.max_size(); 　            返回set容器可能包含的元素最大个数，107374182
    s.size(); 　　　　          返回当前set容器中的元素个数
    s.rbegin;　　　　           返回迭代器,返回的值和end()相同
    s.rend();　　　　           返回迭代器,返回的值和rbegin()相同
    s.insert(1);                在s中插入元素1
    s.count(x);                 返回bool，因为一个键值在set只可能出现0或1次，即判断某一键值x是否在set出现过
    s.erase(iterator);          删除定位器iterator指向的值
    s.erase(first,second);      左闭右开，删除定位器first和second之间的值
    s.erase(key_value);         删除键值key_value的值
    s.find(key_value);          返回给定值的定位器，如果没找到则返回end()
    s.equal_range(key);         //返回一对定位器，分别表示第一个大于或等于给定关键值的元素 和 第一个大于给定关键值 的元素，
                                //这个返回值是一个pair类型，如果这一对定位器中哪个返回失败，就会等于end()的值
    insert(key_value);          //将key_value插入到set中，返回值是pair<set<int>::iterator,bool>，
                                //bool标志着插入是否成功，而iterator代表插入的位置，
                                //若key_value已经在set中，则iterator表示的key_value在set中的位置。
    inset(first,second);        //左闭右开
                                //将定位器first到second之间的元素插入到set中，返回值是void.
    s.lower_bound(key_value);   返回第一个大于等于key_value的定位器
    s.upper_bound(key_value);   返回最后一个大于等于key_value的定位器，可再通过*s.upper_bound(key_value);访问元素值
                            
    pair<set<int>::const_iterator,set<int>::const_iterator> pr;
    pr = s.equal_range(3);
    cout<<"第一个大于等于3的数是："<<*pr.first<<endl;
    cout<<"第一个大于3的数是 ：   "<<*pr.second<<endl;
    
    if((iter = s.find(2)) != s.end())  cout<<*iter<<endl;
    //find()用法
    
    set<int>::iterator iter;
    for(iter = s.begin() ; iter != s.end() ; ++iter)  cout<<*iter<<" ";
    //迭代器遍历所有元素
    
    int a[] = {1,2,3};
    set<int> s(a,a+3);
    //通过数组给set赋值
    
    int a[] = {1,2,3};
    s.insert(a,a+3);
    //左闭右开的赋值
    
    pair<set<int>::iterator,bool> pr;
    pr=s.insert(5);
    if(pr.second)  { cout<<*pr.first<<endl; }
    //insert(key_value);的用法
    
