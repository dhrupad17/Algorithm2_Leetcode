# Arithmetic Slices
---
- ## Question:
> An integer array is called arithmetic if it consists of at least three elements and if the difference between any two consecutive elements is the same.
> 
> For example, [1,3,5,7,9], [7,7,7,7], and [3,-1,-5,-9] are arithmetic sequences.
> 
> Given an integer array nums, return the number of arithmetic subarrays of nums.
> 
>- A subarray is a contiguous subsequence of the array.
---
- ## Example:
> Input: nums = [1,2,3,4]
> 
> Output: 3
> 
> Explanation: We have 3 arithmetic slices in nums: [1, 2, 3], [2, 3, 4] and [1,2,3,4] itself.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int numberOfArithmeticSlices(int[] nums) {
        int slices=0;
        for(int i=2,prev=0;i<nums.length;i++)
        {
            if(nums[i]-nums[i-1]==nums[i-1]-nums[i-2])
            {
                prev=prev+1;
                slices=slices+prev;
            }
            else
            {
                prev=0;
            }
        }
        return slices;
    }
}
