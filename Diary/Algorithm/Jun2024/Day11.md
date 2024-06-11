### [1122. Relative Sort Array](https://leetcode.com/problems/relative-sort-array/description/)

```
class Solution:
    def relativeSortArray(self, arr1: List[int], arr2: List[int]) -> List[int]:
        count_map = dict()
        remaining = []
        result = []

        for num in arr2:
            count_map[num] = 0

        for num in arr1:
            if num in count_map:
                count_map[num] += 1
            else:
                remaining.append(num)

        remaining.sort()

        for num in arr2:
            result.extend([num] * count_map[num])

        result.extend(remaining)

        return result
```
