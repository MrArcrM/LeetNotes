

### 215-FindKthLargest

+ [Question](https://leetcode-cn.com/problems/kth-largest-element-in-an-array/)：find the k^th^ largest num in an array

+ My Solution：

  use a min heap with k capacity

```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        arr = nums[0:k]
        heapq.heapify(arr)
        for i in range(k, len(nums)):
            if nums[i] > arr[0]:
                arr[0] = nums[i]
                heapq.heapify(arr)

        return arr[0]        
```

