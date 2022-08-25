# House Robber II
---
- ## Question:
> You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.
> 
> Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.
---
- ## Example:
> Input: nums = [2,3,2]
> 
> Output: 3
> 
> Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int rob(int[] nums) {
        if(nums.length == 0) return 0;
        if(nums.length == 1) return nums[0];
        if(nums.length == 2) return Math.max(nums[0], nums[1]);
        int max = Integer.MIN_VALUE;
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);
        for(int i = 2; i < nums.length - 1; i++){
            dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i]);
        }
        for(int val : dp){
            max = Math.max(max, val);
        }
        if(nums.length < 3) return max;

        dp = new int[nums.length];
        dp[1] = nums[1];
        dp[2] = Math.max(nums[1], nums[2]);
        for(int i = 3; i < nums.length; i++){
            dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i]);
        }
        for(int val : dp){
            max = Math.max(max, val);
        }
        return max;
    }
}
