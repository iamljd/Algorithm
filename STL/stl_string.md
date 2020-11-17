```cpp
//C++引入了ostringstream、istringstream、stringstream这三个类，需包含头文件<sstream>
#include<sstream>
#include<string>
string s;
```

####
    
    s.substr(pos,n);                需要两个参数，第一个是开始位置，第二个是获取子串的长度。
    s.find(value);                  查找某串是否在s中，若无则返回s.end()
    s=s+" ";                        串的连接
    s.erase( res.end()-1 );         去除最后串的最后一个字母
    
    string a = s.substr(0,5);       获得字符串s中从第0位开始的长度为5的字符串
    
    stringstream ss(sentence);
    string temp;
    while(ss>>temp)
    //istringstream去除空格读取sentence中的单词
    
    if( s.find(temp.substr(0,i))!=s.end() ) 
    { temp=temp.substr(0,i); }
    //通过substr查找子串
