# Description

- Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a root-to-leaf path such that adding up all the values along the path equals `targetSum`. A leaf is a node with no children. (`boolean hasPathSum(TreeNode root, int targetSum)`)

# Example

- `[5,4,8,11,null,13,4,7,2,null,null,null,1] and 22 -> true`
<img src="https://assets.leetcode.com/uploads/2021/01/18/pathsum1.jpg" width="400">

- `[1,2,3] and 5 -> false`
<img src="https://assets.leetcode.com/uploads/2021/01/18/pathsum2.jpg" width="400">

- `[] and 0 -> false`

- `[1,-2,3,1,3,-2,null,-1] and -1 -> true`

# Solution

- Solution 1: 

```Java
class Solution {
  public boolean hasPathSum(TreeNode root, int targetSum) {
    return dfs(root, 0, targetSum);
  }
  private boolean dfs(TreeNode root, int currentSum, int targetSum) {
    if (root == null) return false;
    
    currentSum += root.val;
    if (root.left == null && root.right == null) {
      return (currentSum == targetSum);
    }
    
    return dfs(root.left, currentSum, targetSum) || 
          dfs(root.right, currentSum, targetSum);
  }
}
```

- Solution 2: 

```Java
class Solution {
  public boolean hasPathSum(TreeNode root, int sum) {
    if (root == null) return false;
    if (root.val == sum && root.left == null && root.right == null) return true;
    return                                       
        hasPathSum(root.left, sum - root.val) ||
        hasPathSum(root.right, sum - root.val);
  }
}
```
