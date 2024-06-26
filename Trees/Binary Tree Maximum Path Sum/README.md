
# Binary Tree Maximum Path Sum

### Problem Link 
##### https://leetcode.com/problems/binary-tree-maximum-path-sum/description/
### Description
A path in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence at most once. Note that the path does not need to pass through the root.

The path sum of a path is the sum of the node's values in the path.

Given the root of a binary tree, return the maximum path sum of any non-empty path.
```
Example 1:


Input: root = [1,2,3]
Output: 6
Explanation: The optimal path is 2 -> 1 -> 3 with a path sum of 2 + 1 + 3 = 6.
Example 2:


Input: root = [-10,9,20,null,null,15,7]
Output: 42
Explanation: The optimal path is 15 -> 20 -> 7 with a path sum of 15 + 20 + 7 = 42.
 
```

## Solution 
### reference https://www.youtube.com/watch?v=mOdetMWwtoI
### Solution 1
```java
class Solution {
    public int allMax;

    public int maxPathSum(TreeNode root) {
        if(root==null){
            return 0;
        }
        if(root.left==null && root.right==null){
            return root.val;
        }
        allMax = Integer.MIN_VALUE;
        findMax(root);
        return allMax;
    }

    public int findMax(TreeNode root){
        if(root==null){
            return 0;
        }
        allMax = Math.max(allMax,root.val);
        if(root.left==null && root.right==null){
            return root.val;
        }
        int left = Math.max(0,findMax(root.left));
        int right = Math.max(0,findMax(root.right));

        allMax = Math.max(allMax, left+right+root.val);

        return Math.max(left,right)+root.val;
    }
}
```


