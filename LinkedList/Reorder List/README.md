
#   Reorder List

### Problem Link 
##### https://leetcode.com/problems/reorder-list/description/
### Description
You are given the head of a singly linked-list. The list can be represented as:

L0 → L1 → … → Ln - 1 → Ln
Reorder the list to be on the following form:

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …
You may not modify the values in the list's nodes. Only nodes themselves may be changed.
```
Example 1:


Input: head = [1,2,3,4]
Output: [1,4,2,3]
Example 2:


Input: head = [1,2,3,4,5]
Output: [1,5,2,4,3]
```

## Solution 
#### See https://www.youtube.com/watch?v=xRYPjDMSUFw for reference
```java
public void reorderList(ListNode head) {
        if(head == null || head.next == null ) return;
        // head of list 1
        ListNode l1 = head;
        // head of list 2
        ListNode slow = head;
        // tail of list 2
        ListNode fast = head;
        // tail of list 1
        ListNode prev = null;

        while(fast != null && fast.next !=null){
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
            
        }

        prev.next = null;
        ListNode l2 = reverse(slow);
        merge(l1,l2);
        
    }

    private ListNode reverse(ListNode node){
        ListNode currNode = node;
        ListNode prev = null;

        while(currNode!=null){
            ListNode nextNode = currNode.next;
            currNode.next = prev;
            prev = currNode;
            currNode = nextNode;
        }
        return prev;
    }

    private void merge(ListNode l1,ListNode l2){
        while(l1!=null){
            ListNode l1Next = l1.next;
            ListNode l2Next = l2.next;

            l1.next = l2;
            if(l1Next==null) break;

            l2.next = l1Next;
            l1 = l1Next;
            l2 = l2Next;
        }
    }
```



