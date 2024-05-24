# Description

- Given a binary tree, find its minimum depth. The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node. Note: A leaf is a node with no children. (`int  minDepth(TreeNode  root)`)

# Example

- `[3,9,20,null,null,15,7] -> 2`
<img src="https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg" width="400">

- `[2,null,3,null,4,null,5,null,6] -> 5`

# Solution

- Solution 1: Depth first search (not optimal if have long subtree on the left and only 1 leaf on the right $\Rightarrow$ have to traverse all the node on the left first)

```Java
public class Solution {
  public int minDepth(TreeNode root) {
  	if (root == null)	return 0;
  	
  	if (root.left == null)	return minDepth(root.right) + 1;
  	if (root.right == null) return minDepth(root.left) + 1;
  	
  	return Math.min(minDepth(root.left),minDepth(root.right)) + 1;
  }
}
```

- Solution 2: Breath first search

```Java
class Solution {
  public int minDepth(TreeNode root) {
      if (root == null) {return 0;}
      
      Queue<TreeNode> queue = new LinkedList<>();
      queue.add(root);
      int level = 1;
      
      while (!queue.isEmpty()) {
        int size = queue.size();
        for (int i = 0; i < size; i++) {
          TreeNode current = queue.poll();
          //this is a leaf node
          if (current.left == null && current.right == null) {return level;}
          
          if (current.left != null) {queue.add(current.left);}
          if (current.right != null) {queue.add(current.right);}
        }
        level++;
      }
      return level;
  }
}
```
