

### 378-KthSmallest

+ [Question](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/)：find the k<sup>th</sup> smallest element in a row-increasing and col-incresing matrix

+ My Solution：

  use an array to store all elements, sort it, then return arr[k-1]

```python
class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
        if matrix is None or len(matrix) == 0: return -1
        
        arr = []
        for i in range(len(matrix)):
            for j in range(len(matrix[0])):
                arr.append(matrix[i][j])
        
        arr.sort()
        return arr[k-1]
```

