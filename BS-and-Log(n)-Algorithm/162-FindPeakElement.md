

### 162-FindPeakElement

+ [Question](https://leetcode-cn.com/problems/find-peak-element/)：find any index of peak elements in an array

+ Analysis：

  As nums[-1] = nums[n] = -inf，peak num is on the large side(arr[x]) if arr[x] > arr[x+1]. So it can be dealtt with `BinarySearch`

+ Solution：

```python
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return -1

        start = 0
        end = len(nums) - 1
        while start < end:
            mid = int((start + end) / 2)
            if nums[mid] > nums[mid+1]: end = mid
            else: start = mid + 1

        return start
```

