# Max Points on a Line
---
- ## Question:
> Given an array of points where points[i] = [xi, yi] represents a point on the X-Y plane, return the maximum number of points that lie on the same straight line.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/02/25/plane1.jpg)
> Input: points = [[1,1],[2,2],[3,3]]
> 
> Output: 3
---
- ## Solution:
**Code :**
```java
class Solution {
    int ans=0;
    HashMap<String,Integer> map=new HashMap<>();
    public int gcd(int x,int y){
        if(x==0){
            return y;
        }
        return gcd(y%x,x);
    }
    public int maxPoints(int[][] points) {
        for(int i=0;i<points.length;i++){
            map.clear();
            for(int j=i+1;j<points.length;j++){
                int x=points[j][0]-points[i][0];
                int y=points[j][1]-points[i][1];
                String m="";
                if(x==0){
                    m="0";
                }
                else if(y==0){
                    m="1";
                }
                else{
                    int sign=x*y>0?1:-1;
                    int gcd=gcd(Math.abs(x),Math.abs(y));
                    x=Math.abs(x/gcd);
                    y=Math.abs(y/gcd);
                    if(sign>0){
                        m=String.valueOf(x)+"#"+String.valueOf(y);
                    }
                    else{
                        m="-"+String.valueOf(x)+"#"+String.valueOf(y);
                    }
                }
                map.put(m,map.getOrDefault(m,0)+1);
                ans=Math.max(ans,map.get(m));
            }
        }
        return ans+1;
    }
}
