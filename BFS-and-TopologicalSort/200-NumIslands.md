

### 200-NumIslands

+ [Question](https://leetcode-cn.com/problems/number-of-islands/)：find num of islands in a 2-D array

+ Analysis：

  Find a start point, then update all island to 0 using [`BFS`](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/). 

  Loop it and record the loop number, until the grid is all updated as 0.

+ My Solution：

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        count = 0
        if grid is None or len(grid) == 0: return count

        p = self.getStartPoint(grid, 0, 0)
        while p[0] != -1 and p[1] != -1:
            grid = self.update(grid, p[0], p[1])
            p = self.getStartPoint(grid, p[0], p[1])
            count += 1
        return count

    def getStartPoint(self, grid, x, y):
        rows, cols = len(grid), len(grid[0])
        for i in range(x, rows):
            for j in range(cols):
                if grid[i][j] == '1':
                    return [i, j]
        return [-1, -1]

    def update(self, grid, x, y):
        rows, cols = len(grid), len(grid[0])
        q = []
        q.append([x, y])
        while len(q) > 0:
            p = q.pop()
            i, j = p[0], p[1]
            grid[i][j] = '0'
            if i-1>=0 and grid[i-1][j] == '1': q.append([i-1, j])
            if i+1<rows and grid[i+1][j] == '1': q.append([i+1, j])
            if j-1>=0 and grid[i][j-1] == '1': q.append([i, j-1])
            if j+1<cols and grid[i][j+1] == '1': q.append([i, j+1])

        return grid       
```

