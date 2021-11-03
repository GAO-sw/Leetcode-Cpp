# [Intersection of Two Arrays](https://leetcode-cn.com/problems/intersection-of-two-arrays/)

# 题目
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

#### Example
```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.
```

# 解题思路


# 代码
```
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        if(nums1.empty()||nums2.empty())//特判
        return {};
        sort(nums1.begin(),nums1.end());
        sort(nums2.begin(),nums2.end());
        int index1 = 0,index2 = 0,pre = -1;
        vector<int> Intersection;
        while(index1 < nums1.size() && index2 < nums2.size())
        {
            if(nums1[index1] == nums2[index2])
            {
                if(pre!=nums1[index1])
                {
                    Intersection.emplace_back(nums1[index1]);
                    pre=nums1[index1];
                }
                ++index1;++index2;
            }
            else if(nums1[index1]>nums2[index2])
            ++index2;
            else
            ++index1;
        }
        return Intersection;
    }
};
```
