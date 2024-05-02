
# Kth Smallest Element in a BST

### Problem Link 
##### https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/
### Description
Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.
```
Example 1:


Input: root = [3,1,4,null,2], k = 1
Output: 1
Example 2:


Input: root = [5,3,6,2,4,null,null,1], k = 3
Output: 3
 
```

## Solution 

### Solution 1
```java
class Solution {
    public void inorder(TreeNode root, List<Integer> list){
        if(root==null){
            return;
        }
        inorder(root.left,list);
        list.add(root.val);
        inorder(root.right,list);
    }
    public int kthSmallest(TreeNode root, int k) {
        List<Integer> list = new ArrayList<>();
        inorder(root,list);
        return list.get(k-1);
    }
}
```

## Solution 2
```java
class Solution {
    int count=0,ksmallest=Integer.MIN_VALUE;
    public int kthSmallest(TreeNode root, int k) {
        int[] count=new int[]{0};
           dfs(root,k,count);
           return ksmallest;
      
    }
    void dfs(TreeNode root,int k,int[] count){
       
       if(root==null || count[0]>k){
        return;
       }
        dfs(root.left,k,count);
    
        count[0]++;
        if(k==count[0]){
            ksmallest=root.val;
        }
        dfs(root.right,k,count);
        
    }
}
```
