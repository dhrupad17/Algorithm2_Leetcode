# Jump Game II
---
- ## Question:
> Given an array of non-negative integers nums, you are initially positioned at the first index of the array.
> 
> Each element in the array represents your maximum jump length at that position.
> 
> Your goal is to reach the last index in the minimum number of jumps.
> 
> You can assume that you can always reach the last index.
---
- ## Example:
> Input: nums = [2,3,1,1,4]
> 
> Output: 2
---
- ## Solution:
**Code :**
```java
class Solution {
   public int jump(int[] A) {
    int sc = 0;
    int e = 0;
    int max = 0;
    for(int i=0; i<A.length-1; i++) {
        max = Math.max(max, i+A[i]);
        if( i == e ) {
            sc++;
            e = max;
        } 
    }
    return sc;
}
}
