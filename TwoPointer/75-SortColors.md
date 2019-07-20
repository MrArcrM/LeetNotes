

### 75-SortColors

+ [Question](https://leetcode-cn.com/problems/sort-colors/)：sort 3 colors in an array
+ Solution：

```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        if nums is None or len(nums) == 0: return
        p, r, b = 0, 0, len(nums)-1
        while p <= b:
            if nums[p] == 0:
                nums[r], nums[p] = nums[p], nums[r]
                r += 1
                p += 1
            elif nums[p] == 2:
                nums[b], nums[p] = nums[p], nums[b]
                b -= 1
            elif nums[p] == 1:
                p += 1
```

