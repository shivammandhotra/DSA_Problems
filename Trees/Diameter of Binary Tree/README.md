
# Diameter of Binary Tree

### Problem Link 
##### https://leetcode.com/problems/diameter-of-binary-tree/description/
### Description
Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.
```
Example 1:


Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
Example 2:

Input: root = [1,2]
Output: 1
 
```

## Solution 
#### 

### 
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
    int maxDiameter = Integer.MIN_VALUE;
    public int diameterOfBinaryTree(TreeNode root) {
        diameterOfBinaryTree2(root);
        return maxDiameter;
    }

    public int diameterOfBinaryTree2(TreeNode root) {
        if(root==null){
            return 0;
        }
        int rightLen = diameterOfBinaryTree2(root.right);
        int leftLen = diameterOfBinaryTree2(root.left);
        maxDiameter = Math.max(maxDiameter,rightLen+leftLen);
        return Math.max(rightLen,leftLen)+1;
    }
}
```



