# 3Sum
---
- ## Question:
> Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.
> 
> Notice that the solution set must not contain duplicate triplets.
---
- ## Example:
> Input: nums = [-1,0,1,2,-1,-4]
> 
> Output: [[-1,-1,2],[-1,0,1]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> ans=new ArrayList<>();
        for(int p1=0;p1+2<nums.length;p1++)
        {
            if(p1>0 && nums[p1]==nums[p1-1])
                continue;
        int p2=p1+1;
        int p3=nums.length-1;
        while(p2<p3)
        {
            int sum=nums[p1]+nums[p2]+nums[p3];
            if(sum==0)
            {
                ans.add(Arrays.asList(nums[p1],nums[p2],nums[p3]));
                p3--;
                while(p2<p3 && nums[p3]==nums[p3+1])
                    p3--;
            }
            else if(sum>0)
            {
                p3--;
            }
            else
            {
                p2++;
            }
        }
        }
        return ans;
    }
}
