

### 77-Combine

+ [Question](https://leetcode-cn.com/problems/combinations/)：given n and k, in array {1…n}, find all combinations with k elements
+ My Solution：

```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        res = []

        def helper(idx, count, vec):
            if count == 0:
                res.append(vec)
                return
            elif idx >= n: return
            v = vec.copy()
            v.append(idx+1)
            helper(idx+1, count-1, v)
            helper(idx+1, count, vec)

        helper(0, k, [])
        return res        
```

