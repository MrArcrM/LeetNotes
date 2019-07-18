

### 300-LengthOfLIS

+ [Question](https://leetcode-cn.com/problems/longest-increasing-subsequence/)：find the length of a longest Increasing Subarray
+ My Solution：

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return 0
        elif len(nums) == 1: return 1
        
        maxLen = 0
        for i in range(len(nums)):
            count = 1
            target = nums[i]
            for j in range(i-1):
                if nums[j] < target: 
                    count += 1
                    target = nums[j]
            target = nums[i]
            for j in range(i+1, len(nums)):
                if target < nums[j]: 
                    count += 1
                    target = nums[j]
                    
            maxLen = max(maxLen, count)
        
        return maxLen
```

+ Solution-2：`dp`   O(n<sup>2</sup>) Time

  dp[i]：the max length of subarray which is end of `nums[i]`

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return 0
        elif len(nums) == 1: return 1
        
        dp = [1] * len(nums)
        for i in range(len(nums)):
            for j in range(i):
                if nums[i] > nums[j]:
                    dp[i] = max(dp[i], dp[j]+1)
        
        return max(dp)
```



