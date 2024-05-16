### [2000. Reverse Prefix of Word](https://leetcode.com/problems/reverse-prefix-of-word/description/)

```
class Solution:
    def reversePrefix(self, word: str, ch: str) -> str:
        j = word.find(ch)
        if j != -1:
            return word[:j+1][::-1] + word[j+1:]
        return word
```
