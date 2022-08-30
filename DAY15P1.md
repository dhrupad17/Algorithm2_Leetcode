# Decode Ways
---
- ## Question:
> Given a string s containing only digits, return the number of ways to decode it.
> 
> The test cases are generated so that the answer fits in a 32-bit integer.
---
- ## Example:
> Input: s = "12"
> 
> Output: 2
> 
> Explanation: "12" could be decoded as "AB" (1 2) or "L" (12)
---
- ## Solution:
**Code :**
```java
class Solution {

public int numDecodings(String s) {
    int n=s.length();
    char arr[]=s.toCharArray();
    if(arr[0]=='0')
        return 0;
    int dp[]=new int[n+1];
  
    dp[0]=1;
    dp[1]=arr[0]!='0'?1:0;
    
    for(int i=2;i<n+1;i++)
    {
        int takeone=0,taketwo=0;
        if(arr[i-1]!='0')
        {
        takeone=dp[i-1];
            
        }
       if(arr[i-2]!='0'&&arr[i-2]<='2'&&!(arr[i-2]=='2'&&arr[i-1]>'6'))
       {
         taketwo=dp[i-2];  
       }
    dp[i]=takeone+taketwo;
    }
    
    return dp[n];     
}
}
