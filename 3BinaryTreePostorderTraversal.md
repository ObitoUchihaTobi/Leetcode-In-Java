# Description

- Given the  `root`  of a binary tree, return the postorder traversal of its nodes' values. (`List<Integer> postorderTraversal(TreeNode  root)`)

# Example

- `[1,null,2,3] -> [3,2,1]`
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
  public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    postorder(root, result);
    
    return result;
  }
  
  private void postorder(TreeNode root, List<Integer> result) {
    if (root == null) return;
    
    postorder(root.left, result);
    postorder(root.right, result);
    result.add(root.val);
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
  public List<Integer> postorderTraversal(TreeNode root) {
    Stack<TreeNode> stack = new Stack<>();
    Stack<Boolean> visitSecondTime = new Stack<>();
    
    List<Integer> result = new ArrayList<>();
    
    if (root == null) return result;
  
    stack.add(root);
    visitSecondTime.add(false); //false cause visit the first time
    
    while (!stack.isEmpty()) {
      TreeNode current = stack.pop();
      Boolean visit = visitSecondTime.pop();
      
      // if visit the second then add it to result
      if (visit == true) {result.add(current.val);}
      else {
        stack.add(current);
        visitSecondTime.add(true); //true cause visit the second time
        //add right node first
        if (current.right != null) {
          stack.add(current.right);
          visitSecondTime.add(false);
        }
        if (current.left != null) {
          stack.add(current.left);
          visitSecondTime.add(false);
        }
      }
    }
    return result;
  }
}

```
