# [26.Remove Duplicates from Sorted Array](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)
# 题目
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

#### Example 
```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
```
# 解题思路
![动画](https://user-images.githubusercontent.com/54204224/139885204-6214699c-dd5f-48d7-85f1-6337f3cafc8e.gif)



# 代码
```
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0; 
        int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < (nums.size() - 1); fastIndex++){
            if(nums[fastIndex] != nums[fastIndex + 1]) { 
                nums[++slowIndex] = nums[fastIndex + 1]; 
            }
        }
        return slowIndex + 1; 
    }
};
```
