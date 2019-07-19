

### 11-MaxArea

+ [Question](https://leetcode-cn.com/problems/container-with-most-water/)：find the max area in the pool

+ Solution：

  use two pointers. l = 0, r = len(height)-1. The shorter side will be moved to the longer side. It's a possible way to get new area.

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        res = 0
        l, r = 0, len(height) - 1
        while l < r:
            res = max(res, (r-l)*min(height[l], height[r]))
            if height[l] < height[r]:
                l += 1
            else:
                r -= 1
        
        return res
```

