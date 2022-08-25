# Word Search
---
- ## Question:
> Given an m x n grid of characters board and a string word, return true if word exists in the grid.
> 
> The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2020/11/04/word2.jpg)
> Input: board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean exist(char[][] board, String word) {
        for(int r=0;r<board.length;r++)
        {
            for(int c=0;c<board[0].length;c++)
            {
                if(board[r][c]==word.charAt(0) && help(board,word,0,r,c))
                    return true;
            }
        }
        return false;
    }
    public boolean help(char[][] board,String word, int start, int r, int c)
    {
        if(word.length()<=start)
            return true;
        if(r<0|| c<0|| r>=board.length|| c>=board[0].length|| board[r][c]=='0'|| board[r][c]!=word.charAt(start))
            return false;
        char tmp=board[r][c];
        board[r][c]=0;
        if(help(board,word,start+1,r+1,c) || help(board,word,start+1,r,c+1) || help(board,word,start+1,r-1,c) ||                                       help(board,word,start+1,r,c-1) )
            return true;
        board[r][c]=tmp;
        return false;
    }
}
