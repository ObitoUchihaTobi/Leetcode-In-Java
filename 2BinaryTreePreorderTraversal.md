# Description

- Given the  `root`  of a binary tree, return the preorder traversal of its nodes' values. (`List<Integer> preorderTraversal(TreeNode  root)`)

# Example

- `[1,null,2,3] -> [1,2,3]`
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
  public List<Integer> preorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    preorder(root, result);
    return result;
  }
  
  private void preorder(TreeNode root, List<Integer> result) {
    if (root == null) return;
    
    result.add(root.val);
    preorder(root.left, result);
    preorder(root.right, result);
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
  public List<Integer> preorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<>();
    List<Integer> result = new ArrayList<>();
    
    if (root == null) return result;
    
    stack.add(root);
    while (!stack.isEmpty()) {
      TreeNode currentNode = stack.pop();
      result.add(currentNode.val);
      
      if (currentNode.right != null) stack.add(currentNode.right);
      if (currentNode.left != null) stack.add(currentNode.left);
    }
    
    return result;
  }
}
```
