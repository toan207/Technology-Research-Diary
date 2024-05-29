### [1404. Number of Steps to Reduce a Number in Binary Representation to One](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-in-binary-representation-to-one/)

```
class Solution:
    def numSteps(self, s: str) -> int:
        i = len(s) - 1
        addOne = False
        count = 0

        while i > 0:
            if (s[i] == '1' and not addOne) or (s[i] == '0' and addOne):
                count += 2
                addOne = True
            else:
                count += 1
            i -= 1

        if addOne: count += 1
        return count
```
