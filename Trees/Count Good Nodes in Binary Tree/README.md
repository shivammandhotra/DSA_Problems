
# Count Good Nodes in Binary Tree

### Problem Link 
##### https://leetcode.com/problems/count-good-nodes-in-binary-tree/description/
### Description
Given a binary tree root, a node X in the tree is named good if in the path from root to X there are no nodes with a value greater than X.

Return the number of good nodes in the binary tree.
```
Example 1:



Input: root = [3,1,4,3,null,1,5]
Output: 4
Explanation: Nodes in blue are good.
Root Node (3) is always a good node.
Node 4 -> (3,4) is the maximum value in the path starting from the root.
Node 5 -> (3,4,5) is the maximum value in the path
Node 3 -> (3,1,3) is the maximum value in the path.
Example 2:



Input: root = [3,3,null,4,2]
Output: 3
Explanation: Node 2 -> (3, 3, 2) is not good, because "3" is higher than it.
Example 3:

Input: root = [1]
Output: 1
Explanation: Root is considered as good.
 
```

## Solution 
### Reference https://www.youtube.com/watch?v=G6wBfPgGpPE
### Solution 1
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int count = 0;

    public int goodNodes(TreeNode root) {
        
        dfs(root, Integer.MIN_VALUE);
        return count;
    }

    public void dfs(TreeNode root, int curMax) {
        if (root == null) return;
        
        // Update count if the current node value is greater than or equal to curMax
        if (root.val >= curMax) {
            count++;
            curMax = root.val; // Update curMax
        }
        
        // Recursively traverse left and right subtrees with the updated curMax
        dfs(root.left, curMax);
        dfs(root.right, curMax);
    }
}
```

