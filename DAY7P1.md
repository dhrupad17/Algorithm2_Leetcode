# Populating Next Right Pointers in Each Node II
---
- ## Question:
> Given a binary tree
```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```
> Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.
>
> Initially, all next pointers are set to NULL.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2019/02/15/117_sample.png)
> Input: root = [1,2,3,4,5,null,7]
> 
> Output: [1,#,2,3,#,4,5,7,#]
---
- ## Solution:
**Code :**
```java
class Solution {
	public Node connect(Node root) {
		if(null == root) {
			return null;
		}

		if (root.left != null && root.right != null) {
			root.left.next = root.right;
			root.right.next = findNext(root.next);
		} else if (root.left != null) {
			root.left.next = findNext(root.next);
		} else if (root.right != null) {
			root.right.next = findNext(root.next);
		}

		/**right first*/
		connect(root.right);
		connect(root.left);
		return root;
	}

	private Node findNext(Node root) {
		if (null == root) {
			return null;
		} else if (null != root.left) {
			return root.left;
		} else if (null != root.right) {
			return root.right;
		}
		return findNext(root.next);
	}
}
