### [2285. Maximum Total Importance of Roads](https://leetcode.com/problems/maximum-total-importance-of-roads/)

```
func maximumImportance(n int, roads [][]int) int64 {
    deg := make([]int, n)
	for _, e := range roads {
		deg[e[0]]++
		deg[e[1]]++
	}
	
	sort.Ints(deg)
	var ans int64 = 0
	for i := 0; i < n; i++ {
		ans += int64(i+1) * int64(deg[i])
	}
	return ans
}
```
