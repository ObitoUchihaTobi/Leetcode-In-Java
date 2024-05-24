# Description

- Given the `root` of a binary tree, check whether it is a mirror of itself AKA symmetric around its center. (`boolean  isSymmetric(TreeNode  root)`)

# Example

- `[1,2,2,3,4,4,3] -> true`
<img src="https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg" width="400">

- `[1,2,2,null,3,null,3] -> false`
<img src="https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg" width="400">
- `[2,3,3,4,5,null,4] -> false`
- `[1,0] -> false`
- `[1] -> true`

# Solution

- Solution 1: Recursive approach

```Java
class Solution {
  public boolean isSymmetric(TreeNode root) {
    if (root == null) {return true;}
    return compare(root.left, root.right);
  }
    
  private boolean compare(TreeNode leftNode, TreeNode rightNode) {
    if (leftNode == null && rightNode == null) {return true;}
    if (leftNode == null || rightNode == null) {return false;}
    
    if (leftNode.val != rightNode.val) return false;
    return compare(leftNode.left, rightNode.right) && compare(leftNode.right, rightNode.left);
  }
}
``` 

- Solution 2: Iterative approach

```Java
class Solution {
  public boolean isSymmetric(TreeNode root) {
    if (root == null) {return true;}

    Stack<TreeNode[]> stack = new Stack<>();
    stack.push(new TreeNode[]{root.left, root.right});

    while (!stack.isEmpty()) {
      TreeNode[] nodes = stack.pop();

      if (nodes[0] == null && nodes[1] == null) {continue;}

      if (nodes[0] == null || nodes[1] == null) {return false;}

      if (nodes[0].val != nodes[1].val) {return false;}

      stack.push(new TreeNode[]{nodes[0].left, nodes[1].right});
      stack.push(new TreeNode[]{nodes[0].right, nodes[1].left});
    }

    return true;
  }
}
```
