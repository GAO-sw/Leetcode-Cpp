# [题目](https://leetcode-cn.com/problems/two-sum/)

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order

#### Example
```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Output: Because nums[0] + nums[1] == 9, we return [0, 1].
```

# 解题思路
用双指针，撞针。
先排序 。 排序后原有下标关系会发生变化， 所以要创建一个新的临时数组来储存给定数组。找出所求的数之后，再用临时数组和原数组比较，找到相同的项，返回正确的原始下标。
考虑到会存在重复的项， 需要给找到的项做标记。

# 代码

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> ans;
        vector<int> temp(nums);
        sort(temp.begin(),temp.end());
        int n = temp.size();
        int left = 0;
        int right = n - 1;
        while(left < right){
            if(temp[left] + temp[right] < target)
                left++;
            else if(temp[left] + temp[right] > target)
                right--;
            else break;
        }
        for(int i = 0; i < n; i++){
            if(left != -1 && nums[i] == temp[left]){
                ans.emplace_back(i);
                left = -1;
            }
            else if(right != -1 && nums[i] == temp[right]){
                ans.emplace_back(i);
                right = -1;
            }
            if (left == -1 && right == -1) break;
        }
        return ans;
    }
};
```
