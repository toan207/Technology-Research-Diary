### [409. Longest Palindrome](https://leetcode.com/problems/longest-palindrome/description/)

```
class Solution:
    def longestPalindrome(self, s: str) -> int:
        freq=0
        for c in s:
            freq^=(1<<(ord(c)-ord('A')))
        L=len(s)
        hasOdd=0
        for i in range(58):
            if ((freq>>i)&1)==1: 
                L-=1
                hasOdd=1
        return L+hasOdd
```
