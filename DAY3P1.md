# Remove Duplicates from Sorted List II
---
- ## Question:
> Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.
---
- ## Example:
![alt](https://assets.leetcode.com/uploads/2021/01/04/linkedlist1.jpg)
> Input: head = [1,2,3,3,4,4,5]
> 
> Output: [1,2,5]
---
- ## Solution:
**Code :**
```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head==null)
            return null;
        if(head.next!=null && head.val==head.next.val)
        {
            while(head.next!=null && head.val==head.next.val)
            {
                head=head.next;
            }
            return deleteDuplicates(head.next);
        }
        else
        {
            head.next=deleteDuplicates(head.next);
        }
        return head;
    }
}
