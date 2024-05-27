### [1608. Special Array With X Elements Greater Than or Equal X](https://leetcode.com/problems/special-array-with-x-elements-greater-than-or-equal-x/)

```
class Solution:
    def specialArray(self, nums: List[int]) -> int:
        nums.sort()
        n: int = len(nums)

        def find_number_of_nums(cur_num) -> int:
            left: int = 0
            right: int = n - 1

            first_index: int = n
            while left <= right:
                mid: int = (left + right) // 2

                if nums[mid] >= cur_num:
                    first_index = mid
                    right = mid - 1
                else:
                    left = mid + 1

            return n - first_index

        for candidate_number in range(1, n + 1, 1):
            if candidate_number == find_number_of_nums(candidate_number):
                return candidate_number

        return -1
```
