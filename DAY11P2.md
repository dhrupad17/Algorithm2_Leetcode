# Generate Parentheses
---
- ## Question:
> Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
---
- ## Example:
> Input: n = 3
> 
> Output: ["((()))","(()())","(())()","()(())","()()()"]
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<String> generateParenthesis(int n) {
        ArrayList<String> ans=new ArrayList<>();
        brackets(ans,"",0,0,n);
        return ans;
    }
    public void brackets(ArrayList<String> ans,String p,int open,int close, int n)
    {
        if(p.length()==n*2)
        {
            ans.add(p);
            return;
        }
        if(open<n)
        {
            brackets(ans,p+"(",open+1,close,n);
        }
        if(close<open)
        {
            brackets(ans,p+")",open,close+1,n);
        }
    }
}
