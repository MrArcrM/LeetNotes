

### 264-NthUglyNumber

+ [Question](https://leetcode-cn.com/problems/ugly-number-ii/)：find the Nth ugly number(can only be divided with 2/3/5)
+ Solution：

```python
class Solution:
    def nthUglyNumber(self, n: int) -> int:
        if n <= 0 : return 0

        dp, p2, p3, p5 = [1], 0, 0, 0
        while len(dp) < n:
            dp.append(min(dp[p2]*2, dp[p3]*3, dp[p5]*5))
            while dp[p2]*2 <= dp[-1]:
                p2 += 1
            while dp[p3]*3 <= dp[-1]:
                p3 += 1
            while dp[p5]*5 <= dp[-1]:
                p5 += 1

        return dp[n-1]        
```

