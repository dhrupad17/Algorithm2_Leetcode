# Integer Break
---
- ## Question:
> Given an integer n, break it into the sum of k positive integers, where k >= 2, and maximize the product of those integers.
> 
> Return the maximum product you can get.
---
- ## Example:
> Input: n = 2
> 
> Output: 1
> 
> Explanation: 2 = 1 + 1, 1 × 1 = 1
---
- ## Solution:
**Code :**
```java
class Solution {
    public int integerBreak(int n) {
        int dp[]=new int[n+1];
        if(n==0)
            return 0;
        if(n==1)
            return 1;
        if(n==2)
            return 1;
        if(n==3)
            return 2;
        else
        {
            dp[0]=0;
            dp[1]=1;
            dp[2]=1;
            dp[3]=2;
            int max=0;
            for(int i=4;i<=n;i++)
            {
                for(int j=1;j<i;j++)
                {
                    dp[i]=Math.max(max,(Math.max(dp[i-j],i-j)*Math.max(j,dp[j])));
                    max=dp[i];
                }
            }
        }
        return dp[n];
    }
}
