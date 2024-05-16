### [3075. Maximize Happiness of Selected Children](https://leetcode.com/problems/maximize-happiness-of-selected-children/description/)

```
class Solution:
    def maximumHappinessSum(self, happiness: List[int], k: int) -> int:
        happiness.sort(reverse=True)
        i = 0
        res = 0

        while k > 0:
            happiness[i] = max(happiness[i] - i, 0)
            res += happiness[i]
            i += 1
            k -= 1

        return res
```
