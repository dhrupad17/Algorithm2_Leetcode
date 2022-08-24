# Subsets II
---
- ## Question:
> Given an integer array nums that may contain duplicates, return all possible subsets (the power set).
> 
> The solution set must not contain duplicate subsets. Return the solution in any order.
---
- ## Example:
> Input: nums = [1,2,2]
> 
> Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> res=new ArrayList<>();
        helper(nums,0,res,new ArrayList<>());
        return res;
    }
    public void helper(int[] nums,int pos,List<List<Integer>> res,List<Integer> temp)
    {
        if(pos<=nums.length)
        {
            res.add(new ArrayList<>(temp));
        }
        for(int i=pos;i<nums.length;i++)
        {
            if(i>pos && nums[i]==nums[i-1])
                continue;
            temp.add(nums[i]);
            helper(nums,i+1,res,temp);
            temp.remove(temp.size()-1);
        }
    }
}
