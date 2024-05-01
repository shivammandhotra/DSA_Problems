
# Binary Tree Level Order Traversal

### Problem Link 
##### https://leetcode.com/problems/binary-tree-level-order-traversal/description/description/
### Description
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).
```
Example 1:


Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]
Example 2:

Input: root = [1]
Output: [[1]]
Example 3:

Input: root = []
Output: []
 
```

## Solution 

### Solution 1
```java
public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> que = new LinkedList<>();
        List<List<Integer>> arrayList = new ArrayList<>();

        if(root==null) return arrayList;

        que.add(root);
        while(!que.isEmpty()){
            int size = que.size();
            List<Integer> list = new ArrayList<>();
            for(int i=0;i<size;i++){
                TreeNode node = que.poll();
                list.add(node.val);
                if(node.left!=null){que.add(node.left);}
                if(node.right!=null){que.add(node.right);}
            }
            arrayList.add(list);
        }
        return arrayList;
    }

```
