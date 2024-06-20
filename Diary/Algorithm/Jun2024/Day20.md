### [1552. Magnetic Force Between Two Balls](https://leetcode.com/problems/magnetic-force-between-two-balls/)

```
func canPut(position []int, balls int, force int) bool {
	prev := -int(1e9)

	for _, pos := range position {
		if pos < prev + force {
			continue
		}

		prev = pos
		balls--

		if balls == 0 {
			return true
		}
	}

	return false
}

func maxDistance(position []int, m int) int {
	sort.Ints(position)

	left := 1
	right := int(1e9)
	res := 0

	for left <= right {
		mid := left + (right - left)/2
		if canPut(position, m, mid) {
			res = mid
			left = mid + 1
		} else {
			right = mid - 1
		}
	}

	return res
}
```
