

### 33-Search

+ [Question](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)：find the target number in a rotated array(no duplicates).
+ My Solution：

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        p1, p2 = 0, len(nums)-1
        while p1 <= p2:
            pMid = (p1+p2) // 2
            if nums[pMid] == target: return pMid
            if nums[p1] < nums[pMid]:
                if nums[p1] <= target < nums[pMid]:
                    p2 = pMid - 1
                else: p1 = pMid + 1
            elif nums[pMid] < nums[p2]:
                if nums[pMid] < target <= nums[p2]:
                    p1 = pMid + 1
                else: p2 = pMid - 1
            else:
                p1 += 1
        return -1
```

