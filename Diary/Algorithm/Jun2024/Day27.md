### [1791. Find Center of Star Graph](https://leetcode.com/problems/find-center-of-star-graph/)

```
func findCenter(edges [][]int) int {
    if edges[0][0] != edges[1][0] && edges[0][0] != edges[1][1] { return edges[0][1] }
    return edges[0][0]
}
```
