# Find First and Last Position of Element in Sorted Array
---
- ## Question:
> Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.
> 
> If target is not found in the array, return [-1, -1].
> 
> You must write an algorithm with O(log n) runtime complexity.
---
- ## Example:
> Input: nums = [5,7,7,8,8,10], target = 8
> 
> Output: [3,4]
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int[] ans={-1,-1};
        int startI=search(nums,target,true);
        int endI=search(nums,target,false);
        ans[0]=startI;
        ans[1]=endI;
        return ans;
    }
    int search(int[] nums,int target,boolean starti)
    {
        int ans=-1;
        int start=0;
        int end=nums.length-1;
        while(start<=end)
        {
            int mid=start+(end-start)/2;
            if(nums[mid]>target)
            {
                end=mid-1;
            }
            else if(nums[mid]<target)
            {
                start=mid+1;
            }
            else
            {
                ans=mid;
                if(starti)
                {
                    end=mid-1;
                }
                else
                {
                    start=mid+1;
                }
            }
        }
        return ans;
    }
}
