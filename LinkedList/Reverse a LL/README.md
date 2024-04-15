
# Reverse Linked List

### Problem Link 
##### https://leetcode.com/problems/reverse-linked-list/description/

### Description
Given the head of a singly linked list, reverse the list, and return the reversed list.
 
```
Example 1:


Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]

Example 2:


Input: head = [1,2]
Output: [2,1]

Example 3:

Input: head = []
Output: []
```

## Solution 

```java
public ListNode reverseList(ListNode head) {
        if(head==null || head.next==null) return head;
        ListNode curr = head,temp=null,next;

        while(curr.next!=null){
            next = curr.next;
            curr.next = temp;
            temp = curr;
            curr = next;
        }
        curr.next = temp;
        return curr;
    }
```
