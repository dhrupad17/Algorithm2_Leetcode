# Longest Common Subsequence
---
- ## Question:
> Given two strings text1 and text2, return the length of their longest common subsequence. If there is no common subsequence, return 0.
> 
> A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.
> 
>- For example, "ace" is a subsequence of "abcde".
>
> A common subsequence of two strings is a subsequence that is common to both strings.
---
- ## Example:
> Input: text1 = "abcde", text2 = "ace" 
> 
> Output: 3
>   
> Explanation: The longest common subsequence is "ace" and its length is 3.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int longestCommonSubsequence(String s1, String s2) {
         int x=s1.length();
         int y=s2.length();
         int dp[][]=new int[x+1][y+1];
        return lcsUtil(x,y,s1,s2,dp);
    }
    static int lcsUtil(int x,int y,String s1,String s2,int dp[][])
    {
        for(int i=1;i<=x;i++)
        {
            for(int j=1;j<=y;j++)
            {
                if(s1.charAt(i-1)==s2.charAt(j-1)){
                    dp[i][j]=dp[i-1][j-1]+1;
                }
                else
                {
                    dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return dp[x][y];
    }
}
