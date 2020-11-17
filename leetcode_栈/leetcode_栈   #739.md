739. 每日温度   //中等
-------
    请根据每日 气温 列表，重新生成一个列表。对应位置的输出为：要想观测到更高的气温，至少需要等待的天数。如果气温在这之后都不会升高，请在该位置用 0 来代替。

    例如，给定一个列表 temperatures = [73, 74, 75, 71, 69, 72, 76, 73]，你的输出应该是 [1, 1, 4, 2, 1, 1, 0, 0]。

    提示：气温 列表长度的范围是 [1, 30000]。每个气温的值的均为华氏度，都是在 [30, 100] 范围内的整数。
    
链接:https://leetcode-cn.com/problems/daily-temperatures/submissions/

Code:
```cpp
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& T) 
    {
        int n=T.size();
        vector<int> res(n,0);
        stack<int> s;
        for(int i=0;i<n;i++)
        {
            while( !s.empty() && T[i]>T[s.top()] )
            {
                auto it=s.top();
                s.pop();
                res[it]=i-it;
            }
            s.push(i);
        }
        return res;
    }
};
```

#####
思路分析
* 单调栈只遍历一次O(n²)->O(n)，当遇到比栈top小的入栈等待处理，栈非空且遇到比栈top大的就pop
#####
用时
执行用时：
* 124 ms, 在所有 C++ 提交中击败了76.52%的用户
* 内存消耗：39.2 MB, 在所有 C++ 提交中击败了16.60%的用户
* 2020/11/18   0:25
