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

https://leetcode-cn.com/problems/intersection-of-two-arrays/solution/pai-xu-shuang-zhi-zhen-yi-ci-bian-li-by-solitary-s/


runtime beats 89.43%
memory usage beats 90.58%
# 代码
```
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        vector<int> ans; 
        sort(nums1.begin(),nums1.end());
        sort(nums2.begin(),nums2.end());
        int place1=0;
        int place2=0;
        while(place1<nums1.size() && place2<nums2.size()){
            if(nums1[place1]==nums2[place2]){
                if(ans.size()==0){
                    ans.push_back(nums1[place1]);
                }
                else{
                    int len=ans.size()-1;
                    if(nums1[place1]!=ans[len]){
                        ans.push_back(nums1[place1]);
                    }
                }
                place1++;
                place2++;
            else if(nums1[place1]<nums2[place2]){ 
                place1++;
            }else{
                place2++;
            }
        }
        return ans;
    }
};
```
