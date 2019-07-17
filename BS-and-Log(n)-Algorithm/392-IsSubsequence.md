

### 392-IsSubsequence

+ [Question](https://leetcode-cn.com/problems/is-subsequence/)：
+ My Solution：

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        p1 = p2 = 0
        while p2 < len(t):
            if p1 == len(s): 
                return True
            if s[p1] == t[p2]:
                p1 += 1
            p2 += 1
        
        if p1 == len(s): return True
        return False
```

