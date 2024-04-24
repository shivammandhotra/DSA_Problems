
#   Remove Nth Node From End of List

### Problem Link 
##### https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/
### Description
Given the head of a linked list, remove the nth node from the end of the list and return its head.
```
Example 1:


Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
Example 2:

Input: head = [1], n = 1
Output: []
Example 3:

Input: head = [1,2], n = 1
Output: [1]
```

## Solution 

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
 // int count = 0;
        // ListNode currNode = head;
        // ListNode prevNode = null;

        // while(currNode != null && count != n){
        //     count++;
        //     prevNode = currNode;
        //     currNode = currNode.next;
        // }

        // if(currNode != null){
        //     prevNode.next = currNode.next;
        // }
        // return head;  
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        int count = 0;
        ListNode currNode = head;
        ListNode prevNode = null;
        while(currNode != null){
            count++;
            currNode = currNode.next;
        }
        int i = count - n;
        if(i==0){
            head = head.next;
        }
        else{
            prevNode = head;
            while(i-1!=0){
                prevNode = prevNode.next;
                i--;
            }
            prevNode.next = prevNode.next.next;
        }
        return head;
    }
}

```



