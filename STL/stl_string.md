```cpp
//C++引入了ostringstream、istringstream、stringstream这三个类，需包含头文件<sstream>
#include<sstream>
#include<string>
string s;
```

####
    
    s.substr(i,j);                  左闭右闭,s的子串，返回string类
    s.find(value);                  查找某串是否在s中，若无则返回s.end()
    s=s+" ";                        串的连接
    s.erase( res.end()-1 );         去除最后串的最后一个字母
    
    stringstream ss(sentence);
    string temp;
    while(ss>>temp)
    //istringstream去除空格读取sentence中的单词
    
    if( s.find(temp.substr(0,i))!=s.end() ) 
    { temp=temp.substr(0,i); }
    //通过substr查找子串
