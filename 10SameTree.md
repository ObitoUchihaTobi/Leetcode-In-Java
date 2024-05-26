# Description

- Given the roots of two binary trees  `p`  and  `q`, write a function to check if they are the same or not. Two binary trees are considered the same if they are structurally identical, and the nodes have the same value. (`boolean isSameTree(TreeNode p, TreeNode q)`)

# Example

- `[1,2,3] and [1,2,3] -> true`
<img src="https://assets.leetcode.com/uploads/2020/12/20/ex1.jpg" width="400">

- `[1,2] and [1,null,2] -> false`
<img src="https://assets.leetcode.com/uploads/2020/12/20/ex2.jpg" width="400">

- `[1,2,1] and[1,1,2]-> false`
<img src="https://assets.leetcode.com/uploads/2020/12/20/ex3.jpg" width="400">



# Solution

```Java
class Solution {
  public boolean isSameTree(TreeNode p, TreeNode q) {
    if (p == null && q == null) return true;
    if (p == null || q == null) return false;
    if (p.val != q.val) return false;
    
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
  }
}

//class TreeNode {
//   int val;
//   TreeNode left;
//   TreeNode right;
//   TreeNode() {}
//   TreeNode(int val) { this.val = val; }
//   TreeNode(int val, TreeNode left, TreeNode right) {
//     this.val = val;
//     this.left = left;
//     this.right = right;
//   }
// }
```
