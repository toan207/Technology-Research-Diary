### [1038. Binary Search Tree to Greater Sum Tree](https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/)

```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func bstToGst(root *TreeNode) *TreeNode {
    sum := 0
    dfs(root, &sum)
    return root
}

func dfs(root *TreeNode, sum *int) {
    if root == nil { return }
    dfs(root.Right, sum)
    *sum += root.Val
    root.Val = *sum
    dfs(root.Left, sum)
}
```
