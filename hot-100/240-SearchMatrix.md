

### 240-SearchMatrix

+ [Question](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/)：search a target in a matrix whose left is always smaller than right, and top is always smaller than bottom

+ My Solution：

  O(m+n) Time

```python
class Solution:
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        if matrix is None or len(matrix) == 0 or len(matrix[0]) == 0: return False
        pi, pj = 0, len(matrix[0])-1
        while pi < len(matrix) and pj >= 0:
            if matrix[pi][pj] == target: return True
            elif matrix[pi][pj] > target: pj -= 1
            else: pi += 1

        return False        
        
```

