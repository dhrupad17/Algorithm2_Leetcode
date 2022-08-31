# Coin Change
---
- ## Question:
> Given an integer n, break it into the sum of k positive integers, where k >= 2, and maximize the product of those integers.
> 
> Return the maximum product you can get.
---
- ## Example:
> You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.
> 
> Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.
> 
> You may assume that you have an infinite number of each kind of coin.
---
- ## Solution:
**Code :**
```java
class Solution {
    public int coinChange(int[] coins, int amount){
    if(coins == null || coins.length == 0 || amount < 1) return 0;

    Deque<Integer> queue = new ArrayDeque<Integer>();
    Set<Integer> visited = new HashSet<Integer>();
    queue.addFirst(amount);
    visited.add(amount);
    int level = 0;

    while(!queue.isEmpty()){
      int size = queue.size();

      while(size-- > 0){
        int curr = queue.removeLast();
        if(curr == 0) return level;

        if(curr < 0) continue;

        for(int coin : coins){
          int next = curr - coin;
          if(next >= 0 && !visited.contains(next)){
            queue.addFirst(next);
            visited.add(next);
          }
        }
      }

      level++;
    }

    return -1;
  }

}
