

### 121-MaxProfit

+ [Question](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)：only one transaction for max profit
+ My Solution：

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if prices is None or len(prices) == 0: return 0

        maxP = 0
        minNum = prices[0]
        for i in range(1, len(prices)):
            maxP = max(maxP, prices[i] - minNum)
            minNum = min(minNum, prices[i])

        return maxP  
```

