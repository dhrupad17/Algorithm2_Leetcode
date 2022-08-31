# Delete Operation for Two Strings
---
- ## Question:
> Given two strings word1 and word2, return the minimum number of steps required to make word1 and word2 the same.
> 
> In one step, you can delete exactly one character in either string.
---
- ## Example:
> Input: word1 = "sea", word2 = "eat"
> 
> Output: 2
> 
> Explanation: You need one step to make "sea" to "ea" and another step to make "eat" to "ea".
---
- ## Solution:
**Code :**
```java
class Solution {
    public int minDistance(String word1, String word2) {
    int dp[][] = new int[word1.length()+1][word2.length()+1];
    for(int i = 0; i <= word1.length(); i++) {
        for(int j = 0; j <= word2.length(); j++) {
            if(i == 0 || j == 0) dp[i][j] = 0;
            else dp[i][j] = (word1.charAt(i-1) == word2.charAt(j-1)) ? dp[i-1][j-1] + 1
                    : Math.max(dp[i-1][j], dp[i][j-1]);
        }
    }
    int val =  dp[word1.length()][word2.length()];
    return word1.length() - val + word2.length() - val;
}
}
