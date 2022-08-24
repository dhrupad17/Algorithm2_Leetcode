# Subsets
---
- ## Question:
> Given an integer array nums of unique elements, return all possible subsets (the power set).
> 
> The solution set must not contain duplicate subsets. Return the solution in any order.
---
- ## Example:
> Input: nums = [1,2,3]
> 
> Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> ret= new ArrayList<>();
        dfs(nums,0,new ArrayList<>(),ret);
        return ret;
    }
    public void dfs(int nums[], int indx, List<Integer>path ,List<List<Integer>>ret)
    {
        ret.add(path);
        
        for(int i=indx; i<nums.length;i++)
        {List<Integer> p= new ArrayList<>(path);
            p.add(nums[i]);
            dfs(nums,i+1,p,ret);
        }
    }
}
