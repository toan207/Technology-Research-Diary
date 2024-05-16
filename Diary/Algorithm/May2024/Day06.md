### [2487. Remove Nodes From Linked List](https://leetcode.com/problems/remove-nodes-from-linked-list/description/)

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseLinkedList(self, head):
        prev_node = None
        current_node = head
        next_node = None

        # Reverse the linked list
        while current_node:
            next_node = current_node.next
            current_node.next = prev_node
            prev_node = current_node
            current_node = next_node
        
        return prev_node

    def removeNodes(self, head: Optional[ListNode]) -> Optional[ListNode]:
        head = self.reverseLinkedList(head)

        max_value = 0
        prev_node = None
        current_node = head

        while current_node:
            max_value = max(max_value, current_node.val)

            if current_node.val < max_value:
                prev_node.next = current_node.next
                deleted_node = current_node
                current_node = current_node.next
                deleted_node.next = None

            else:
                prev_node = current_node
                current_node = current_node.next
        
        return self.reverseLinkedList(head)
```
