
#   Copy List with Random Pointer

### Problem Link 
##### https://leetcode.com/problems/copy-list-with-random-pointer/description/
### Description
A linked list of length n is given such that each node contains an additional random pointer, which could point to any node in the list, or null.

Construct a deep copy of the list. The deep copy should consist of exactly n brand new nodes, where each new node has its value set to the value of its corresponding original node. Both the next and random pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. None of the pointers in the new list should point to nodes in the original list.

For example, if there are two nodes X and Y in the original list, where X.random --> Y, then for the corresponding two nodes x and y in the copied list, x.random --> y.

Return the head of the copied linked list.

The linked list is represented in the input/output as a list of n nodes. Each node is represented as a pair of [val, random_index] where:

val: an integer representing Node.val
random_index: the index of the node (range from 0 to n-1) that the random pointer points to, or null if it does not point to any node.
Your code will only be given the head of the original linked list.
```
Example 1:


Input: head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
Output: [[7,null],[13,0],[11,4],[10,2],[1,0]]
Example 2:


Input: head = [[1,1],[2,1]]
Output: [[1,1],[2,1]]
Example 3:



Input: head = [[3,null],[3,0],[3,null]]
Output: [[3,null],[3,0],[3,null]]
 
```

## Solution 
#### See https://www.youtube.com/watch?v=q570bKdrnlw&t=576s for reference
### solution 1
```java
private Node mapRandomList(Node head){
        Node temp = head;
        Map<Node,Node> hashMap = new HashMap<>();
        while(temp!=null){
            Node newNode = new Node(temp.val);
            hashMap.put(temp, newNode);
            temp = temp.next;
        }
        temp = head;

        while(temp!=null){
            Node copyNode = hashMap.get(temp);
            copyNode.next = hashMap.get(temp.next);
            copyNode.random = hashMap.get(temp.random);
            temp = temp.next;
        }
        return hashMap.get(head);
    }

```
#### Time complexity O(N)
#### space complexity O(N)

### solution 2

```java
private Node optimised(Node head){
        // step 1 Insert copy node in between
        Node temp = head;
        while(temp!=null){
            Node copyNode = new Node(temp.val);
            copyNode.next = temp.next;
            temp.next = copyNode;
            temp = temp.next.next;
        }
        // step 2 connect randoms
        temp = head;
        while(temp!=null){
            Node copyNode = temp.next;
            if(temp.random==null){
                copyNode.random = null;
                temp = temp.next.next;
                continue;
            }
            copyNode.random = temp.random.next;
            temp = temp.next.next;
        }
        // inserting next and disconnecting
        Node dNode = new Node(-1);
        Node res = dNode;
        temp = head;
        while(temp!=null){
            res.next = temp.next;
            temp.next = temp.next.next;
            res = res.next;
            temp = temp.next;
        }
        return dNode.next;
    }

```
#### Time complexity O(N)
#### space complexity O(1)


