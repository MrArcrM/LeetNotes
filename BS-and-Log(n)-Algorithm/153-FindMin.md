

### 153-FindMin

+ [Question](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)：find min in a sorted and rotated array
+ My Solution：

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return -1
        pStart = 0
        pEnd = len(nums) - 1
        while pStart + 1 < pEnd and nums[pStart] > nums[pEnd]:
            pMid = int((pStart + pEnd) / 2)
            if nums[pStart] > nums[pMid]:
                pEnd = pMid
            elif nums[pMid] > nums[pEnd]:
                pStart = pMid
        return min(nums[pStart], nums[pEnd])        
```

+ Related：

  🏷 [`81-Search`](./81-Search.md)

  