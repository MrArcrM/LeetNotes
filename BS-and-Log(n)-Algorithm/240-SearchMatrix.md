

### 240-SearchMatrix

+ [Question](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/)：

+ My Solution：

  same as [74-SearchMatrix](74-SearchMatrix.md)

```python
class Solution:
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        if matrix is None or len(matrix) == 0: return False
        i, j = 0, len(matrix[0])-1
        while i < len(matrix) and j >= 0:
            if matrix[i][j] == target: 
                return True
            elif target > matrix[i][j]: 
                i += 1
            else: j -= 1
                
        return False
```

