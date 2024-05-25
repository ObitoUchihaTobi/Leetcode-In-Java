# Description

- Given the `root` of a binary tree, invert the tree, and return its root (`TreeNode invertTree(TreeNode  root)`).

# Example

- `[4,2,7,1,3,6,9] -> [4,7,2,9,6,3,1]`
<img src="https://assets.leetcode.com/uploads/2021/03/14/invert1-tree.jpg" width="400">

- `[2,1,3] -> [2,3,1]`
<img src="https://assets.leetcode.com/uploads/2021/03/14/invert2-tree.jpg" width="400">

- `[] -> []`

# Solution

- Solution 1: Recursive approach

```Java
class Solution {
  public TreeNode invertTree(TreeNode root) {
    if (root == null) return null;
    
    TreeNode tempNode = root.right;
    root.right = root.left;
    root.left = tempNode;
    
    invertTree(root.left);
    invertTree(root.right);
    
    return root;
  }
}
```

- Solution 2: Iterative approach

```Java
class Solution {
  public TreeNode invertTree(TreeNode root) {
    if(root == null) {return null;}
    
    Queue<TreeNode> q = new LinkedList<TreeNode>();
    q.add(root);
    while(!q.isEmpty()){
      TreeNode temp = q.poll();
      
      if(temp.left != null) {q.add(temp.left);}
      if(temp.right != null) {q.add(temp.right);}
      
      TreeNode curr = temp.left;
      temp.left = temp.right;
      temp.right = curr;
    }
    return root;
  }
}
```
