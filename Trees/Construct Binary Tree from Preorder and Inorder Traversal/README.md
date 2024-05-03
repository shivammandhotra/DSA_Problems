
# Construct Binary Tree from Preorder and Inorder Traversal

### Problem Link 
##### https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/
### Description
Given two integer arrays preorder and inorder where preorder is the preorder traversal of a binary tree and inorder is the inorder traversal of the same tree, construct and return the binary tree.
```
Example 1:


Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
Output: [3,9,20,null,null,15,7]
Example 2:

Input: preorder = [-1], inorder = [-1]
Output: [-1]
 
```

## Solution 
### reference https://www.youtube.com/watch?v=aZNaLrVebKQ
### Solution 1
```java
class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        Map<Integer,Integer> inMap = new HashMap<>();
        for(int i=0;i<inorder.length;i++){
            inMap.put(inorder[i],i);
        }
        TreeNode root = builder(preorder,0,preorder.length-1,inorder,0,inorder.length-1,inMap);
        return root;
    }

    private TreeNode builder(int[] preorder,int preStart,int preEnd,int[] inorder,int inStart,int inEnd, Map<Integer,Integer> inMap){
        if(preStart>preEnd || inStart>inEnd){
            return null;
        }
        TreeNode root = new TreeNode(preorder[preStart]);
        int inRoot = inMap.get(root.val);
        int leftNums = inRoot - inStart;

        root.left = builder(preorder,preStart+1,preStart+leftNums,inorder,inStart,inRoot-1,inMap);
        root.right = builder(preorder,preStart+leftNums+1,preEnd,inorder,inRoot+1,inEnd,inMap);

        return root;
    }
}
```


