

### 221-MaximalSquare

+ [Question](https://leetcode-cn.com/problems/maximal-square/)：find the maximal square of an array whose value is '1' or '0'

+ Solution-1：

  `Equation of state transition`：dp(i, j) = min(dp(i-1, j), dp(i, j-1), dp(i-1, j-1)) + 1

  O(mn) Time, O(mn) Space

```python
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        if matrix is None: return 0
        rows = len(matrix)
        if rows == 0: return 0
        cols = len(matrix[0])
        if cols == 0: return 0
        dp = [[0 for _ in range(cols)] for _ in range(rows)]

        maxLen = 0
        for i in range(rows):
            dp[i][0] = int(matrix[i][0])
            maxLen = max(maxLen, dp[i][0])
        for j in range(cols):
            dp[0][j] = int(matrix[0][j])
            maxLen = max(maxLen, dp[0][j])

        for i in range(1, rows):
            for j in range(1, cols):
                if matrix[i][j] == '1':
                    dp[i][j] = min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1]) + 1
                    maxLen = max(maxLen, dp[i][j])

        return maxLen * maxLen        
```

+ Solution-2：

  Solution-1 Space Optimization

  O(mn) Time, O(n) Space

```python
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        if matrix is None: return 0
        rows = len(matrix)
        if rows == 0: return 0
        cols = len(matrix[0])
        if cols == 0: return 0
        dp = [0] * (cols+1)

        maxLen = 0
        prev = 0
        # for j in range(cols):
        #     dp[j] = int(matrix[0][j])
        #     maxLen = max(maxLen, dp[j])
        for i in range(1, rows+1):
            for j in range(1, cols+1):
                tmp = dp[j]
                if matrix[i-1][j-1] == '1':
                    dp[j] = min(dp[j], dp[j-1], prev) + 1
                    maxLen = max(maxLen, dp[j])
                else:
                    dp[j] = 0
                prev = tmp

        return maxLen * maxLen       
```

+ Related：

  🏷 [`516-LongestPalindromeSubseq`](../BS-and-Log(n)-Algorithm/516-LongestPalindromeSubseq.md)

