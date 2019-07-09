

### 300-LengthOfLIS

+ [Question](https://leetcode-cn.com/problems/longest-increasing-subsequence/)：find the length of Largest Incresing Subsequence
+ My Solution：

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return 0
        dp = [1] * len(nums)
        maxLen = 1
        for i in range(1, len(nums)):
            for j in range(i):
                if nums[j] < nums[i]:
                    dp[i] = max(dp[i], dp[j]+1)
            maxLen = max(maxLen, dp[i])

        return maxLen       
```

