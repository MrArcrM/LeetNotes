

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

+ Solution-2：`BinarySearch`

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        if matrix is None or len(matrix) == 0: return False
        
        m = len(matrix)
        n = len(matrix[0])
        p1, p2 = 0, m*n-1
        while p1 <= p2:
            pMid = (p1 + p2) // 2
            row = pMid // n
            col = pMid % n
            if matrix[row][col] == target: return True
            elif matrix[row][col] > target: p2 = pMid - 1
            else: p1 = pMid + 1
        
        return False
```

+ Solution-3：use `target` in `list()`

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        row = len(matrix)
        for i in range(row):
            if target in matrix[i]:
                return True
        
        return False
```

