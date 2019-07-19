

### 3-LengthOfLongestSubstring

+ [Question](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)：find the length of longest substring with no duplicates
+ My Solution：

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if s is None or len(s) == 0: return 0
        res = p1 = p2 = 0
        for p2 in range(len(s)):
            if self.hasDuplicate(s[p1:p2+1]):
                res = max(res, p2-p1)
                p1 += 1
            else:
                p2 += 1
        
        if not self.hasDuplicate(s[p1:p2-1]):
            res = max(res, p2-p1)
        
        return res
    
    def hasDuplicate(self, s):
        seen = set()
        for ch in s:
            if ch in seen:
                return True
            seen.add(ch)
        
        return False
```

