# Find Minimum in Rotated Sorted Array
---
- ## Question:
> Suppose an array of length n sorted in ascending order is rotated between 1 and n times. For example, the array nums = [0,1,2,4,5,6,7] might become:
> 
>- [4,5,6,7,0,1,2] if it was rotated 4 times.
>- [0,1,2,4,5,6,7] if it was rotated 7 times.
> Notice that rotating an array [a[0], a[1], a[2], ..., a[n-1]] 1 time results in the array [a[n-1], a[0], a[1], a[2], ..., a[n-2]].
> 
> Given the sorted rotated array nums of unique elements, return the minimum element of this array.
> 
> You must write an algorithm that runs in O(log n) time.
---
- ## Example:
> Input: nums = [3,4,5,1,2]
> 
> Output: 1
> 
> Explanation: The original array was [1,2,3,4,5] rotated 3 times.
---
- ## Solution:
**Code :**
```java
public class Solution {
    public int findMin(int[] num) {
        if (num == null || num.length == 0) {
            return 0;
        }
        if (num.length == 1) {
            return num[0];
        }
        int start = 0, end = num.length - 1;
        while (start < end) {
            int mid = (start + end) / 2;
            if (mid > 0 && num[mid] < num[mid - 1]) {
                return num[mid];
            }
            if (num[start] <= num[mid] && num[mid] > num[end]) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return num[start];
    }
}
