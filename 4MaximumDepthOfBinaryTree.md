# Description

- Given the  `root`  of a binary tree, return its maximum depth. A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node. (`int  maxDepth(TreeNode  root)`)

# Example

- `[3,9,20,null,null,15,7] -> 3`
<img src="https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg" width="400">

- `[1,null,2] -> 2`

# Solution

- Solution 1: Recursive depth first search 
```Java
class Solution {
  public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    
    int depthLeft = maxDepth(root.left) + 1;
    int depthRight = maxDepth(root.right) + 1;
    return (depthLeft >= depthRight) ? depthLeft : depthRight;
  }
}
```

- Solution 2: Breath first search

```Java
class Solution {
  public int maxDepth(TreeNode root) {
    Queue<TreeNode> queue = new LinkedList<>();
    
    if (root == null) return 0;
    queue.add(root);
    
    int level = 0;
    while (!queue.isEmpty()) {
      int size = queue.size();
      for (int i = 0;i < size; i++) { 
        TreeNode current = queue.poll();
        if (current.left != null) {queue.add(current.left);}
        if (current.right != null) {queue.add(current.right);}
      }
      level++;
    }
    return level;
  }
}
```

- Solution 3: Iterative depth first search

```Java
class Solution {
  public int maxDepth(TreeNode root) {
    Stack<TreeNode> stack = new Stack<>();
    Stack<Integer> depthStack = new Stack<>();
    
    if (root == null) return 0;
    stack.add(root);
    depthStack.add(1);
    
    int result = 1;
    while (!stack.isEmpty()) {
      TreeNode current = stack.pop();
      int depthLevel = depthStack.pop();
      
      result = (result >= depthLevel) ? result : depthLevel;
      
      if (current.right != null) {
        stack.add(current.right);
        depthStack.add(depthLevel+1);
      }
      if (current.left != null) {
      stack.add(current.left);
      depthStack.add(depthLevel+1);
      }
    }
    return result;
  }
}
```
