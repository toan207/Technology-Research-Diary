### [1051. Height Checker](https://leetcode.com/problems/height-checker/description/)

```
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        return sum(h1 != h2 for h1, h2 in zip(heights, sorted(heights)))
```
