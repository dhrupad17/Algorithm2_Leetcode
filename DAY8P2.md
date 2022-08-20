# Surrounded Regions
---
- ## Question:
> Given an m x n matrix board containing 'X' and 'O', capture all regions that are 4-directionally surrounded by 'X'.
> 
> A region is captured by flipping all 'O's into 'X's in that surrounded region.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2021/02/19/xogrid.jpg)
> Input: board = [["X","X","X","X"],["X","O","O","X"],["X","X","O","X"],["X","O","X","X"]]
>
> Output: [["X","X","X","X"],["X","X","X","X"],["X","X","X","X"],["X","O","X","X"]]
---
- ## Solution:
**Code :**
```java
class Solution {
    public class pair{
        int row;
        int col;
        pair(int row,int col){
            this.row = row;
            this.col = col;
        }
    }
    public void solve(char[][] board) {
        int n = board.length,m = board[0].length;
        int [][] dir = {{0,1},{1,0},{0,-1},{-1,0}};
        LinkedList<pair> que = new LinkedList<>();
        for(int r = 0;r < n;r++){
            if(board[r][0] == 'O'){
                board[r][0] = '+';
                que.addLast(new pair(r,0));
            }
            
            if(board[r][m - 1] == 'O'){
                board[r][m - 1] = '+';
                que.addLast(new pair(r,m - 1));
            }
        }
        
        for(int c = 0; c < m;c++){
            if(board[0][c] == 'O'){
                board[0][c] = '+';
                que.addLast(new pair(0,c));
            }
            
            if(board[n - 1][c] == 'O'){
                board[n - 1][c] = '+';
                que.addLast(new pair(n - 1,c));
            }
        }
        while(que.size() != 0){
            pair rp = que.removeFirst();
            int row = rp.row;
            int col = rp.col;
            
            for(int[] d : dir){
                int r = row + d[0];
                int c = col + d[1];
                
                if(r >= 0 && c >= 0 && r < n && c < m && board[r][c] == 'O'){
                    board[r][c] = '+';
                    que.addLast(new pair(r,c));
                }
            }
        }
        for(int i = 0;i < n;i++){
            for(int j = 0;j < m;j++){
                if(board[i][j] == 'O')  board[i][j] = 'X';
                else if(board[i][j] == '+')  board[i][j] = 'O'; 
            }
        }
    }
}
