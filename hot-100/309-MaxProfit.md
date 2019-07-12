

### 309-MaxProfit

+ [Question](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)：max profix to sell stock with one-day frozen period.

+ My Solution：

  O(n<sup>2</sup>) Time, O(n) Space

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if prices is None or len(prices) == 0: return 0

        dp = [0] * len(prices)
        for i in range(len(prices)-2, -1, -1):
            sum = dp[i+1]
            for j in range(i+1, len(prices)):
                if prices[j] - prices[i] > 0:
                    if j+2 < len(prices):
                        sum = max(sum, prices[j]-prices[i]+dp[j+2])
                    else:
                        sum = max(sum, prices[j]-prices[i])
            dp[i] = sum

        return dp[0]        
```



