

### 34-SearchRange

+ [Question](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)：find first and last index of the target in an array (has duplicates).

+ My Solution：

  Binary Search，then use two pointer to get the most left and most right index.

```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        p1, p2 = 0, len(nums) - 1
        while p1 <= p2:
            pMid = (p1 + p2) // 2
            if nums[pMid] == target:
                pLeft = pRight = pMid
                while pLeft >= 0 and nums[pLeft] == target:
                    pLeft -= 1
                while pRight < len(nums) and nums[pRight] == target:
                    pRight += 1
                return [pLeft+1, pRight-1]
            elif nums[pMid] < target:
                p1 = pMid + 1
            else:
                p2 = pMid - 1
        return [-1, -1]
```

