# Shortest Path in Binary Matrix
---
- ## Question:
> Given an n x n binary matrix grid, return the length of the shortest clear path in the matrix. If there is no clear path, return -1.
> 
> A clear path in a binary matrix is a path from the top-left cell (i.e., (0, 0)) to the bottom-right cell (i.e., (n - 1, n - 1)) such that:
> 
>- All the visited cells of the path are 0.
>- All the adjacent cells of the path are 8-directionally connected (i.e., they are different and they share an edge or a corner).
>
> The length of a clear path is the number of visited cells of this path.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2021/02/18/example1_1.png)
> Input: grid = [[0,1],[1,0]]
> 
> Output: 2
---
- ## Solution:
**Code :**
```java
class Solution {

class Pair{
    int x;
    int y;
    int count;
    
    Pair(int x, int y, int count){
        this.x = x;
        this.y = y;
        this.count = count;
    }
}


public int shortestPathBinaryMatrix(int[][] grid) {
    
    return BFS(grid, 0, 0, grid.length-1, grid[0].length-1);
    
}


public int BFS(int grid[][], int start_x, int start_y , int target_x, int target_y){
    
    Queue<Pair> q = new LinkedList<>();
  
    q.add(new Pair(start_x, start_y, 1));
    
    while(q.size()>0){
        
        Pair rem = q.remove();
        int x = rem.x;
        int y = rem.y;
        int count = rem.count;
       
if(x>=0 && y>=0 && x<grid.length && y<grid[0].length && grid[x][y]!=1 ){
        
        grid[x][y] = 1;
            
        if(x==target_x && y== target_y)
            return rem.count;
        
        q.add(new Pair(x-1, y, count+1 ));
        q.add(new Pair(x-1, y+1, count+1));
        q.add(new Pair(x, y+1 , count+1));
        q.add(new Pair(x+1, y+1, count+1));
        q.add(new Pair(x+1, y, count+1));
        q.add(new Pair(x+1, y-1, count+1));
        q.add(new Pair(x, y-1, count+1));
        q.add(new Pair(x-1, y-1, count+1));
            
      }

   }
    return -1;
}
}
