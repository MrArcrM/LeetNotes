### 139-WordBreak

+ [Question](https://leetcode-cn.com/problems/word-break/)：can a string be splited by wordDict in which word can be used for more than one time

+ Solution：

```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        maxlen = 0
        for word in wordDict:
            maxlen = max(maxlen, len(word))

        res = [0] * len(s)
        for i in range(len(s)):
            p = i
            while (p >= 0 and i - p <= maxlen):
                if (res[p] == 1 and s[p + 1:i + 1] in wordDict) \
                		or (p == 0 and s[p:i + 1] in wordDict):
                    res[i] = 1
                    break
                p -= 1

        return res[-1] == 1
```

