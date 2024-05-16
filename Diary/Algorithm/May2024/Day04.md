### [881. Boats to Save People](https://leetcode.com/problems/boats-to-save-people/description/)

```
class Solution:
    def numRescueBoats(self, people: List[int], limit: int) -> int:
        people.sort()

        left = 0 
        right = len(people) - 1 
        boats_count = 0

        while left <= right:
            if people[left] + people[right] <= limit:
                boats_count += 1  
                left += 1  
                right -= 1  
            elif people[right] <= limit:
                boats_count += 1  
                right -= 1  

        return boats_count 
```
