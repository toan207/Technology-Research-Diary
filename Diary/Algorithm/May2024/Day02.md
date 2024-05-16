### [2441. Largest Positive Integer That Exists With Its Negative](https://leetcode.com/problems/largest-positive-integer-that-exists-with-its-negative/description/)

```
class Solution:
    def findMaxK(self, nums: List[int]) -> int:
        nums.sort()
        n = len(nums)
        for i in range(n-1, -1, -1):
            if nums[i] > 0 and -nums[i] in nums:
                return nums[i]
        return -1 
```
