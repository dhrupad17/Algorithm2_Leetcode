# Word Break
---
- ## Question:
> Given a string s and a dictionary of strings wordDict, return true if s can be segmented into a space-separated sequence of one or more dictionary words.
> 
> Note that the same word in the dictionary may be reused multiple times in the segmentation.
---
- ## Example:
> Input: s = "leetcode", wordDict = ["leet","code"]
> 
> Output: true
> 
> Explanation: Return true because "leetcode" can be segmented as "leet code".
---
- ## Solution:
**Code :**
```java
class Solution {
    HashMap<String,Boolean>map=new HashMap<>();
    public boolean wordBreak(String s, List<String> ls) {
        if(ls.contains(s))
            return true;
        if(map.containsKey(s))
            return map.get(s);
        for(int i=0;i<s.length();i++)
        {
            String left=s.substring(0,i);
            if(ls.contains(left)&&wordBreak(s.substring(i),ls))
            {
                map.put(s,true);
                return true;
            }
        }
        map.put(s,false);
        return false;
    }
}
