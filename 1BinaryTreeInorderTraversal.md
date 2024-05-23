# Description

- Given the  `root`  of a binary tree, return the inorder traversal of its nodes' values. (`List<Integer> inorderTraversal(TreeNode  root)`)

# Example

- `[1,null,2,3] -> [1,3,2]`
<img src="https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg" width="400" height="400">

- `[] -> [] ` 

- `[1] -> [1]`

# Solution

- Solution 1: Recursive solution

```Java
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

class Solution {
  public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();

    inorder(root, result);
    return result;        
  }

  private void inorder(TreeNode node, List<Integer> result) {
    if (node == null) {return;}
    
    inorder(node.left, result);
    result.add(node.val);
    inorder(node.right, result);
  }    
}
```

- Solution 2: Iterative solution (use stack)

```Java
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

class Solution {
  public List<Integer> inorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<>();
    List<Integer> result = new ArrayList<>();
    
    while (root != null || !stack.isEmpty()) {
      while (root != null) {
        stack.push(root);
        root = root.left;
      }
      root = stack.pop();
      result.add(root.val);
      root = root.right;
    }

    return result;
  }
}
```
