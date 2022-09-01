# Shuffle an Array
---
- ## Question:
> Given an integer array nums, design an algorithm to randomly shuffle the array. All permutations of the array should be equally likely as a result of the shuffling.
> 
> Implement the Solution class:
> 
>- Solution(int[] nums) Initializes the object with the integer array nums.
>- int[] reset() Resets the array to its original configuration and returns it.
>- int[] shuffle() Returns a random shuffling of the array.
---
- ## Example:
> Input
["Solution", "shuffle", "reset", "shuffle"]
[[[1, 2, 3]], [], [], []]
>
> Output
[null, [3, 1, 2], [1, 2, 3], [1, 3, 2]]
---
- ## Solution:
**Code :**
```java
class Solution {
    private int[] original;
    private int[] copy;
    private Random random=new Random();
    public Solution(int[] nums) {
        original=nums.clone();
        copy=nums;
    }
    
    public int[] reset() {
        return original;
    }
    
    public int[] shuffle() {
        int index=random.nextInt(copy.length-1);
        int t=copy[index];
        copy[index]=copy[copy.length-1];
        copy[copy.length-1]=t;
        return copy;
    }
}
