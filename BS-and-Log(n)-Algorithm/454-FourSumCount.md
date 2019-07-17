

### 454-FourSumCount

+ [Question](https://leetcode-cn.com/problems/4sum-ii/)：given A, B, C, D, find amount of instance A[i] + B[j] + C[k] + D[l] = 0

+ Solution：

  use a dict `d[ A[i] + B[j]]` = times of appearance, when `0 - C[k] - C[l]` appear in d.keys(), count += d[0 - C[k] - C[l]]

```python
class Solution:
    def fourSumCount(self, A: List[int], B: List[int], C: List[int], D: List[int]) -> int:
        d = {}
        for i in range(len(A)):
            for j in range(len(B)):
                key = A[i] + B[j]
                if key in d.keys():
                    d[key] += 1
                else:
                    d[key] = 1
        
        count = 0
        for k in range(len(C)):
            for l in range(len(D)):
                key = 0 - (C[k] + D[l])
                if key in d.keys():
                    count += d[key]
        
        return count
```



