# Subtree of Another Tree
---
- ## Question:
> Given the roots of two binary trees root and subRoot, return true if there is a subtree of root with the same structure and node values of subRoot and false otherwise.
> 
> A subtree of a binary tree tree is a tree that consists of a node in tree and all of this node's descendants. The tree tree could also be considered as a subtree of itself.
---
- ## Example:
![ALT](https://assets.leetcode.com/uploads/2021/04/28/subtree1-tree.jpg)
> Input: root = [3,4,5,1,2], subRoot = [4,1,2]
> 
> Output: true
---
- ## Solution:
**Code :**
```java
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if(root == null && subRoot == null) return true;
        if(root == null || subRoot == null) return false;
        return checkEqual(root, subRoot) || isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }
    
    private boolean checkEqual(TreeNode root, TreeNode subRoot) {
        if(root == null && subRoot == null) return true;
        if(root == null || subRoot == null) return false;
        return root.val == subRoot.val && checkEqual(root.left, subRoot.left) && checkEqual(root.right, subRoot.right);
    }
}
