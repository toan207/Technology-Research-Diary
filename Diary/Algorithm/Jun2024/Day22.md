### [1248. Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)

```
class Solution:
    def numberOfSubarrays(self, nums: List[int], k: int) -> int:
        res = count = l = 0
        for r in range(len(nums)):
            if nums[r] % 2:
                k -= 1
                count = 0
            while not k:
                k += (nums[l] % 2)
                count += 1
                l += 1
            res += count
        return res
```
