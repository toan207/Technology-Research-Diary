### [260. Single Number III](https://leetcode.com/problems/single-number-iii/submissions/1273454021/)

```
class Solution:
    def singleNumber(self, nums: List[int]) -> List[int]:
        xor_sum = 0
        for num in nums:
            xor_sum ^= num

        set_bit = xor_sum & -xor_sum


        num1, num2 = 0, 0
        for num in nums:
            if num & set_bit:
                num1 ^= num
            else:
                num2 ^= num

        return [num1, num2]
```
