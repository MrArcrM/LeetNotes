

### 131-Partition

+ [Question](https://leetcode-cn.com/problems/palindrome-partitioning/)：partition a Palindrome to be Palindromes
+ Solution：

```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        split_result = []
        if len(s) == 0:
            return split_result

        def back(start=0, res=[]):
            if start >= len(s):
                split_result.append(res)
                return
            for end in range(start + 1, len(s) + 1):
                split_s = s[start:end]
                if split_s == s[start:end][::-1]:
                    back(end, res + [split_s])

        back()
        return split_result        
```

