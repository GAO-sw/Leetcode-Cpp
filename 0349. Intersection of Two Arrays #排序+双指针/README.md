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
# 代码
```
class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        vector<int> ans; //记录最终的答案
        sort(nums1.begin(),nums1.end());//对nums1进行排序
        sort(nums2.begin(),nums2.end());//对nums2进行排序
        int place1=0;//记录nums1数值的下标
        int place2=0;//记录nums2数值的下标

        //对nums1和nums2进行数值比较
        while(place1<nums1.size() && place2<nums2.size()){
            //当两个数相等时
            if(nums1[place1]==nums2[place2]){
                //如果当前ans数组中没有放入数字，则直接放，然后更新place1和place2
                if(ans.size()==0){
                    //将相同的数字放入数组ans
                    ans.push_back(nums1[place1]);
                }
                //如果当前的ans中有数字，为了避免重复，则当前数和前一个数进行比较
                else{
                    int len=ans.size()-1;
                    //如果当前数和前一个数不相等，则存入数组ans中，否则不存
                    if(nums1[place1]!=ans[len]){
                        ans.push_back(nums1[place1]);
                    }
                }

                //更新place1和place2，同时向后移一位
                place1++;
                place2++;
            }//如果两数不相等，则移动小的那个下标
            else if(nums1[place1]<nums2[place2]){ 
                place1++;
            }else{
                place2++;
            }
        }
        //返回最终结果数组
        return ans;

    }
};
```
