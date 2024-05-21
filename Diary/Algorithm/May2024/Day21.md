### [78. Subsets](https://leetcode.com/problems/subsets/submissions/1264166842/)

```
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = [[]]
        stack = []

        for i in range(len(nums)):
            stack.append([[nums[i]], i])

        while stack:
            top, index = stack.pop()
            res.append(top)
            for i in range(index + 1,len(nums)):
                stack.append([top + [nums[i]], i])
            
        return res
```
