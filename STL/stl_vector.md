```cpp
#include<vector>
```
    vector< vector<bool> >  pd(a,vector<bool>(b,false));                    通过二维vector方式产生a×b矩阵
    
    bool** pd;                                                              //通过
	pd = new bool* [a];                                                     //数组的方式
	for (int i = 0; i < a; i++)                                             //new一个
	pd[i] = new bool[b];                                                    //a×b矩阵
    
    void DFS(int n, int s, vector< vector<bool> > &pd) {...}                vector传参              
