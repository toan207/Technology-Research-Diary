### [2816. Double a Number Represented as a Linked List](https://leetcode.com/problems/double-a-number-represented-as-a-linked-list/description/)

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def traceback(self, root):
        if not root: return 0

        tmp = self.traceback(root.next)
        doubleIt = int(root.val) * 2 + tmp
        root.val = doubleIt % 10
        
        return doubleIt // 10
    def doubleIt(self, head: Optional[ListNode]) -> Optional[ListNode]:
        res = self.traceback(head)
        if res != 0:
            tmp = ListNode(res, head)
            head = tmp
        return head
```
