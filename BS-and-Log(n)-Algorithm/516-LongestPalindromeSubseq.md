

### 516-LongestPalindromeSubseq

+ [Question](https://leetcode-cn.com/problems/longest-palindromic-subsequence/)：length of the longest palindrome among a string's permutations

+ Analysis：

  `dp(i,j)`: the longestPalindromeSubseq between s[i] and s[j]

  Equation of State Transition:

  ![image-20190701134212087](../pic/516-Equation.png)

  Return: `dp(0, n-1)`

+ Solution-1：

  O(n<sup>2</sup>) Time, O(n<sup>2</sup>) Space

```python
class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:
        """
        dp(i, j): the longestPalindromeSubseq between s[i] and s[j]

        Equation of State Transition:
                        | dp(i+1, j-1) + 2, if s[i] == s[j]
            dp(i, j) =  |
                        | max(dp(i+1,j), dp(i, j+1)), if s[i] != s[j]

        Return: dp(0, n-1)
        """
        if s is None or len(s) == 0: return 0
        n = len(s)
        dp = [[0 for _ in range(n)] for _ in range(n)]

        for i in range(n-1, -1, -1):
            for j in range(i, n):
                if i == j: dp[i][j] = 1  # set diagonal num to 1
                elif s[i] == s[j]: dp[i][j] = dp[i+1][j-1] + 2
                elif s[i] != s[j]: dp[i][j] = max(dp[i+1][j], dp[i][j-1])

        return dp[0][n-1]        
```

+ Solution-2：

  O(n<sup>2</sup>) Time, O(n) Space

```python
class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:
        if s is None or len(s) == 0: return 0
        n = len(s)
        dp = [0] * n
        prev = 0
        for i in range(n-1, -1, -1):
            for j in range(i, n):
                tmp = dp[j]
                if i == j: dp[j] = 1
                elif s[i] == s[j]: dp[j] = prev + 2
                elif s[i] != s[j]: dp[j] = max(dp[j], dp[j-1])
                prev = tmp
        return dp[-1]        
```

+ Related：

  🏷 [`221-MaximalSquare`](../hot-100/221-MaximalSquare.md)

