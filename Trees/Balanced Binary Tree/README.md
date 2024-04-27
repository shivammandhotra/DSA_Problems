
# Balanced Binary Tree

### Problem Link 
##### https://leetcode.com/problems/balanced-binary-tree/description/
### Description
Given a binary tree, determine if it is 
height-balanced
.
```
Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: true
Example 2:


Input: root = [1,2,2,3,3,null,null,4,4]
Output: false
Example 3:

Input: root = []
Output: true
 
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

    public int height(TreeNode root){
        if(root==null){
            return 0;
        }
        int lh = height(root.left);
        int rh = height(root.right);
        return Math.max(lh,rh)+1;
    }
    public boolean isBalanced(TreeNode root) {
        if(root==null){
            return true;
        }
        int lh = height(root.left);
        int rh = height(root.right);

        return Math.abs(lh-rh)<=1 && isBalanced(root.left) && isBalanced(root.right);
    }
}
```



