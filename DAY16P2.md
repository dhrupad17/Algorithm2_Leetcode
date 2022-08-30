# Number of Longest Increasing Subsequence
---
- ## Question:
> Given an integer array nums, return the number of longest increasing subsequences.
> 
> Notice that the sequence has to be strictly increasing.
---
- ## Example:
> Input: nums = [1,3,5,4,7]
> 
> Output: 2
> 
> Explanation: The two longest increasing subsequences are [1, 3, 4, 7] and [1, 3, 5, 7].
---
- ## Solution:
**Code :**
```java
class Solution {
    public int findNumberOfLIS(int[] nums) {
        return help(nums);
    }
    private int help(int[] arr)
    {
        int n=arr.length;
        int dp[]=new int[n];
        int count[]=new int[n];
        int max=1;
        for(int i=0;i<n;i++)
        {
            dp[i]=1;
            count[i]=1;
        for(int p=0;p<i;p++)
        {
            if(arr[p]<arr[i] && 1+dp[p]>dp[i])
            {
                dp[i]=1+dp[p];
                count[i]=count[p];
            }
            else if(arr[p]<arr[i] && 1+dp[p]==dp[i])
            {
                count[i]+=count[p];
            }
        }
        max=Math.max(max,dp[i]);
        }
        int res=0;
        for(int i=0;i<n;i++)
        {
            if(dp[i]==max)
                res=res+count[i];
        }
        return res;
    }
}
