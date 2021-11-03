# [题目](https://leetcode-cn.com/problems/remove-element/)
Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The relative order of the elements may be changed.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

#### Example
```
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
Note that the five elements can be returned in any order.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

# 解题思路
![动画](https://user-images.githubusercontent.com/54204224/140169720-be4f00a4-f0db-47d9-9599-1dd481d7d34d.gif)
设定快慢两根指针，快指针依次遍历，除非快指针碰到给定值，否则不断将新的所指值赋给慢指针且慢指针右移一位。
用除给定元素外的所有元素覆盖原有元素。
最后返回慢指针,新数组的最后一个元素下标为 slow-1。


# 代码
```
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        if (nums.empty()) return 0;
        int slow = 0;
        for(int fast = 0; fast < nums.size(); fast++){
            if(nums[fast] != val){
                nums[slow++] = nums[fast];
            }
        }
        return slow;
    }
};
```
