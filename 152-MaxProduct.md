

### 152-MaxProduct

+ [Question](https://leetcode-cn.com/problems/maximum-product-subarray/)：max product of subarray with O(n) time and O(1) space

+ Solution：

  Min num may turn to max num because of negative sign. 

  Keep a record of both min and max num can solve it.

  It's a trick to swap min and max num when meeting negative num.

```python
class Solution(object):
    def maxProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums is None or len(nums) == 0: return 0
        maxP = imax = imin = nums[0]
        for i in range(1, len(nums)):
            if nums[i] < 0: imax, imin = imin, imax
            imax = max(imax * nums[i], nums[i])
            imin = min(imin * nums[i], nums[i])
            maxP = max(maxP, imax)

        return maxP  
```

