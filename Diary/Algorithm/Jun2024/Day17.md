### [633. Sum of Square Numbers](https://leetcode.com/problems/sum-of-square-numbers/)

```
class Solution:
    def judgeSquareSum(self, c: int) -> bool:
        divisor = 2
        while divisor * divisor <= c:
            if c % divisor == 0:
                exponentCount = 0
                while c % divisor == 0:
                    exponentCount += 1
                    c //= divisor
                if divisor % 4 == 3 and exponentCount % 2 != 0:
                    return False
            divisor += 1
        return c % 4 != 3
```
