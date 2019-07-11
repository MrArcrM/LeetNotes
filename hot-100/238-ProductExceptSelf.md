

### 238-ProductExceptSelf

+ [Question](https://leetcode-cn.com/problems/product-of-array-except-self/)：calculate product except self in an array. O(n) Time. O(1) Space. Cannot use division.
+ Solution：

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        output = [1] * len(nums)
        for i in range(1, len(nums)):
            output[i] = output[i-1] * nums[i-1]
        product = 1
        for i in range(len(nums)-1, -1, -1):
            output[i] *= product
            product *= nums[i]
        return output       
```

