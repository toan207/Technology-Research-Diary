### [1382. Balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/)

```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def balanceBST(self, root):
        def in_order_traversal(node):
            if not node:
                return []

            return in_order_traversal(node.left) + [node.val] + in_order_traversal(node.right)

        def build_balanced_bst(elements):
            if not elements:
                return None
            mid = len(elements) // 2
            node = TreeNode(elements[mid])
            node.left = build_balanced_bst(elements[:mid])
            node.right = build_balanced_bst(elements[mid + 1:])
            return node

        sorted_elements = in_order_traversal(root)
        return build_balanced_bst(sorted_elements)
        
```
