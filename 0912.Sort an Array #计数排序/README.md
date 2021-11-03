# [0912.Sort an array](https://leetcode-cn.com/problems/sort-an-array/)
# 题目
Given an array of integers nums, sort the array in ascending order.
#### Example

```
Input: nums = [5,1,1,2,0,0]
Output: [0,0,1,1,2,5] 
```

# 解题思路




https://zhuanlan.zhihu.com/p/270158986


```
class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        int max = nums[0];
        int min = nums[0];
        for(int i = 1; i < nums.size(); i++){
            if(max < nums[i])
                max = nums[i];
            if(min > nums[i])  
                min = nums[i];
        }
        vector<int> countarray(max-min+1,0);
        for(int i = 0; i < nums.size(); i++)
            countarray[nums[i]-min]++;
        int k = 0;
        for(int i = 0; i < max-min+1; i++){
            while(countarray[i]--){
                nums[k++] = i + min;
            }
        }
        return nums;
    }
};
```
