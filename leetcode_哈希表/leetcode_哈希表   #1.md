1. 两数之和   //简单
------
    给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

    你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。
    
    示例:

    给定 nums = [2, 7, 11, 15], target = 9

    因为 nums[0] + nums[1] = 2 + 7 = 9
    
    所以返回 [0, 1]
链接:https://leetcode-cn.com/problems/two-sum/

Code:
```cpp
class Solution 
{
public:
    vector<int> twoSum(vector<int>& nums, int target) 
    {
        unordered_map<int,int> mp;
        vector<int> res;
        for(int i=0;i<nums.size();i++)
        {
            if(mp.count(target-nums[i]))
            {
                res={mp[target-nums[i]],i};
                break;
            }
            mp[nums[i]]=i;
        }
        return res;
    }
};
```
#####
思路分析
* 从前往后遍历，对每个元素先往前找mp中有无target-nums[i]、再标记该元素
#####
用时
* 执行用时: 224 ms
* 内存消耗: 51.8 MB
* 2020/11/16   23:04
