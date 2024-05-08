
# Serialize and Deserialize Binary Tree

### Problem Link 
##### https://leetcode.com/problems/serialize-and-deserialize-binary-tree/description/
### Description
Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

Clarification: The input/output format is the same as how LeetCode serializes a binary tree. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.
```
Example 1:
Input: root = [1,2,3,null,null,4,5]
Output: [1,2,3,null,null,4,5]

Example 2:
Input: root = []
Output: []
 
```

## Solution 
### reference neetcode

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Codec {
    private int i;

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        List<String> list =  new ArrayList<>();
        serializeDFS(root,list);
        return String.join(",",list);
    }

    private void serializeDFS(TreeNode root, List<String> list){
        if(root==null){
            list.add("N");
            return;
        }
        list.add(String.valueOf(root.val));
        serializeDFS(root.left,list);
        serializeDFS(root.right,list);
    }

    public TreeNode deserializeDFS(String[] tokens){
        String token = tokens[this.i];
        if(token.equals("N")){
            this.i++;
            return null;
        }
        var node = new TreeNode(Integer.parseInt(token));
        this.i++;
        node.left = deserializeDFS(tokens);
        node.righAt = deserializeDFS(tokens);
        return node;
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        String[] tokens = data.split(",");
        return deserializeDFS(tokens);
    }
}

// Your Codec object will be instantiated and called as such:
// Codec ser = new Codec();
// Codec deser = new Codec();
// TreeNode ans = deser.deserialize(ser.serialize(root));
```


