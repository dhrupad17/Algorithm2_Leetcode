# Interval List Intersections
---
- ## Question:
> You are given two lists of closed intervals, firstList and secondList, where firstList[i] = [starti, endi] and secondList[j] = [startj, endj]. Each list of intervals is pairwise disjoint and in sorted order.
> 
> Return the intersection of these two interval lists.
> 
> A closed interval [a, b] (with a <= b) denotes the set of real numbers x with a <= x <= b.
> 
> The intersection of two closed intervals is a set of real numbers that are either empty or represented as a closed interval. For example, the intersection of [1, 3] and [2, 4] is [2, 3].
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2019/01/30/interval1.png)
> Input: firstList = [[0,2],[5,10],[13,23],[24,25]], secondList = [[1,5],[8,12],[15,24],[25,26]]
> 
> Output: [[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public int[][] intervalIntersection(int[][] firstList, int[][] secondList) {
        List<int[]> temp = new LinkedList<>();
        int p1 = 0, p2 = 0;
        while (p1 < firstList.length && p2 < secondList.length) {
            int[] int1 = firstList[p1], int2 = secondList[p2];
            int start = Math.max(int1[0], int2[0]);
            int end = Math.min(int1[1], int2[1]);
            
            if (start <= end) temp.add(new int[]{start, end});
            if (int1[1] < int2[1]) p1++;
            else p2++;
        }
        
        int[][] res = new int[temp.size()][2];
        int i = 0;
        for (int[] interval : temp) {
            res[i++] = interval;
        }
        return res;
    }
}
