# Description

- You are given the  `root`  of a binary search tree (BST) and an integer `val`. Find the node in the BST that the node's value equals  `val`  and return the subtree rooted with that node. If such a node does not exist, return `null`. (`TreeNode  searchBST(TreeNode  root, int  val)`)

# Example

- `[4,2,7,1,3] and 2 -> [2,1,3]`
<img src="https://assets.leetcode.com/uploads/2021/01/12/tree1.jpg" width="400">

- `[4,2,7,1,3] and 5 -> []`

# Solution

```Java
class Solution {
    public TreeNode searchBST(TreeNode root, int val) {
      if (root == null || root.val == val) return root;
      
		  if (root.val > val) return searchBST(root.left, val); 
		  return searchBST(root.right, val);
    }
}
```
