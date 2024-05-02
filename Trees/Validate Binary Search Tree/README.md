
# Validate Binary Search Tree

### Problem Link 
##### https://leetcode.com/problems/validate-binary-search-tree/description/
### Description
Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:

The left 
subtree
 of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.
```
Example 1:


Input: root = [2,1,3]
Output: true
Example 2:


Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
 
```

## Solution 

### Solution 1
```java
public boolean isValidBST(TreeNode root) {
        if(root==null){
            return true;
        }
        if(root.right != null && root.right.val <= root.val){
            return false;
        }
        if( root.left!=null && root.left.val >= root.val){
            return false;
        }

        return isValidBST(root.left) || isValidBST(root.right);
        
    }
    //this won't work becaues this doesn't checks for the BST validation properly
```

## Solution 2
```java
public boolean isValidBST(TreeNode root) {
        if(root==null){
            return true;
        }
        return dfs(root,null,null);        
    }

    public boolean dfs(TreeNode root, Integer min, Integer max){
        if(root==null){
            return true;
        }

        if((min!=null && root.val<=min)||(max!=null && root.val>=max)){
            return false;
        }

        return dfs(root.left,min,root.val) && dfs(root.right,root.val,max);
    }
```
