

### 209-MinSubArrayLen

+ [Question](https://leetcode-cn.com/problems/minimum-size-subarray-sum/)：min length of the SubArray add up to be >= s

+ Solution-1：TEL

  sums[i] means sum of nums[0…i]. use O(log n) Time to find the first index j s.t. `sums[j] >= s + sums[i] - nums[i]` because of `sums[j] - sums[i] + nums[i] >= s`

  O(nlog n) Time, O(n) Space

```python
class Solution:
    def minSubArrayLen(self, s: int, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return 0
        
        sums = [nums[0]] * len(nums)
        minLen = len(nums) + 1
        for i in range(1, len(nums)):
            sums[i] = sums[i-1] + nums[i]
        
        for i in range(len(nums)):
            toFind = s + sums[i] - nums[i]
            li = list(map(lambda i: i>= toFind, sums[i:]))
            if True in li:
                minLen = min(minLen, li.index(True) + 1)
        
        if minLen > len(nums):
            return 0
        return minLen
```

+ Solution-2：

  use two pointers

  O(n) Time, O(1) Space

```python
class Solution:
    def minSubArrayLen(self, s: int, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return 0
        
        minLen = len(nums) + 1
        left = res = 0
        for i in range(len(nums)):
            res += nums[i]
            while res >= s:
                minLen = min(minLen, i - left + 1)
                res -= nums[left]
                left += 1
        
        if minLen > len(nums):
            return 0
        return minLen
        
        
```

+ 