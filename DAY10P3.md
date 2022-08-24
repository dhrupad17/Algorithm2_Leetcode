# Combination Sum II
---
- ## Question:
> Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.
> 
> Each number in candidates may only be used once in the combination.
> 
> Note: The solution set must not contain duplicate combinations.
---
- ## Example:
> Input: candidates = [10,1,2,7,6,1,5], target = 8
> 
> Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
---
- ## Solution:
**Code :**
```java
class Solution {
    List<List<Integer>> ans=new ArrayList<>();
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<Integer> temp=new ArrayList<>();
        Arrays.sort(candidates);
        check(0,candidates,target,temp);
        return ans;
    }
    public void check(int index,int[] arr,int target,List<Integer> temp)
    {
        if(target==0)
        {
            ans.add(new ArrayList(temp));
            return;
        }
        for(int i=index;i<arr.length;i++)
        {
            if(i>index && arr[i]==arr[i-1])
                continue;
            if(arr[i]>target)
                break;
            temp.add(arr[i]);
            check(i+1,arr,target-arr[i],temp);
            temp.remove(temp.size()-1);
        }
    }
}
