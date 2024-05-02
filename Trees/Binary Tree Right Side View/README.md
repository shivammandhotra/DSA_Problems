
# Binary Tree Right Side View

### Problem Link 
##### https://leetcode.com/problems/binary-tree-right-side-view/description/
### Description
Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.
```
Example 1:


Input: root = [1,2,3,null,5,null,4]
Output: [1,3,4]
Example 2:

Input: root = [1,null,3]
Output: [1,3]
Example 3:

Input: root = []
Output: []
 
```

## Solution 

### Solution 1
```java
// last element in level order traversal
public List<Integer> rightSideView(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<>();
        List<Integer> list = new ArrayList<>();

        if (root == null) return list;

        q.add(root);
        while(!q.isEmpty()){
            int size = q.size();
            for(int i=0;i<size;i++){
                TreeNode node = q.poll();
                if(node.left!=null){
                    q.add(node.left);
                }
                if(node.right!=null){
                    q.add(node.right);
                }
                if(i==size-1){
                    list.add(node.val);
                }
            }
        }
        return list;   
    }
```

### Solution 1
```java
class Solution {
    List<Integer> rightSide = new ArrayList();
    public List<Integer> rightSideView(TreeNode root) {
        
        if(root == null)
           return rightSide;

         helper(root,0);
         return rightSide;  

    }

    public void helper(TreeNode root, int level){
        if(level == rightSide.size())
            rightSide.add(root.val);

         if(root.right!=null){
            helper(root.right,level+1);
         }
         if(root.left!=null){
            helper(root.left,level+1);
         }   
    }
}

```