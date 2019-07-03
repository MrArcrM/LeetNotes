

### 81-Search

+ [Question](https://leetcode-cn.com/problems/search-in-rotated-sorted-array-ii/)：is `target` exist in a sorted and rotated array
+ My Solution：

```python
class Solution:
    def search(self, nums: List[int], target: int) -> bool:
        if nums is None or len(nums) == 0: return False

        start = 0
        end = len(nums) - 1
        while start <= end:
            mid = int((start + end) / 2)
            if nums[mid] == target: return True
            elif nums[mid] > nums[start]:
                if nums[start] <= target < nums[mid]: end = mid - 1
                else: start = mid + 1
            elif nums[mid] < nums[start]:
                if nums[mid] < target <= nums[end]: start = mid + 1
                else: end = mid - 1
            else:
                start += 1

        return False        
```

+ Related

  🏷 [`153-FindMin`](./153-FindMin.md)

  