### [1325. Delete Leaves With a Given Value](https://leetcode.com/problems/delete-leaves-with-a-given-value/)

```
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def dfs(self, root, target):
        if not root: return True
        left = self.dfs(root.left, target)
        right = self.dfs(root.right, target)

        if not left:
            root.left = None
        if not right:
            root.right = None
        
        if root.left == None and root.right == None and root.val == target:
            return False
        return True

    def removeLeafNodes(self, root: Optional[TreeNode], target: int) -> Optional[TreeNode]:
        self.dfs(root, target)
        if root.left == None and root.right == None and root.val == target:
            root = None
        return root
```
