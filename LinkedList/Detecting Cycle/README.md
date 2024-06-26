
# Linked List Cycle

### Problem Link 
##### https://leetcode.com/problems/linked-list-cycle/description/

### Description
Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.
```

Example 1:


Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).

Example 2:


Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 0th node.

Example 3:


Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```

## Solution 1

```java
public boolean hasCycle(ListNode head) {
        if(head==null || head.next==null) return false;
        HashSet<ListNode> hashSet = new HashSet<>();
        ListNode curr = head;
        while(curr!=null){
            if(hashSet.contains(curr)){
                return true;
            }
            hashSet.add(curr);
            curr = curr.next;
        }
        return false;
    }
```

## Solution 2

```java
public boolean hasCycle2(ListNode head) {
        if(head==null || head.next==null) return false;
        ListNode slow = head;
        ListNode fast = head.next;
        while(fast !=null && fast.next!=null){
            fast = fast.next.next;
            slow = slow.next;
            if(slow==fast) return true;
        }
        return false;
    }
```