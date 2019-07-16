

### 74-SearchMatrix

+ [Question](https://leetcode-cn.com/problems/search-a-2d-matrix/)：

+ My Solution：

  ​	use a pivot from `matrix[0][n-1]`，when `target > matrix[i][j]`，i += 1；when `target < matrix[i][j]`, j -= 1.

  ​	O(m+n) Time, O(1) Space

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        if matrix is None or len(matrix) == 0: return False
        m = len(matrix)
        n = len(matrix[0])
        i, j = 0, n-1
        while i < m and j >= 0:
            if matrix[i][j] == target:
                return True
            elif matrix[i][j] < target:
                i += 1
            else:
                j -= 1
        return False
```

