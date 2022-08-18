# Container With Most Water
---
- ## Question:
> You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).
> 
> Find two lines that together with the x-axis form a container, such that the container contains the most water.
> 
> Return the maximum amount of water a container can store.
> 
> Notice that you may not slant the container.
---
- ## Example:
![alt](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)
> Input: height = [1,8,6,2,5,4,8,3,7]
> 
> Output: 49
---
- ## Solution:
**Code :**
```java
class Solution {
    public int maxArea(int[] height) {
        int maxwater=0;
        int left=0;
        int right=height.length-1;
        while(left<right)
        {
            maxwater=Math.max(maxwater,(right-left)*Math.min(height[left],height[right]));
            if(height[left]<height[right])
                left++;
            else
                right--;
        }
        return maxwater;
    }
}
