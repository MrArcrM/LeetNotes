

### 207-CanFinish

+ [Question](https://leetcode-cn.com/problems/course-schedule/)：find if there is a cycle in a Directed Graph
+ Solution：Use `dfs`

```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        if len(prerequisites) == 0: return True

        visited = [0] * numCourses  # 0-never visit, 1-have visited, 2-is visiting
        reverse_adj = [set() for _ in range(numCourses)]  # reverse adjacent list
        for second, first in prerequisites:
            reverse_adj[second].add(first)

        for i in range(numCourses):
            if self.dfs(i, reverse_adj, visited): return False
        return True

    def dfs(self, vertex, reverse_adj, visited):
        """
        :return: True if reverse_adj has cycle, False if not
        """
        if visited[vertex] == 2: return True
        if visited[vertex] == 1: return False

        visited[vertex] = 2  # vertex is visiting
        for precursor in reverse_adj[vertex]:
            if self.dfs(precursor, reverse_adj, visited): return True
        visited[vertex] = 1  # has visited
        return False        
```

