

### 279-NumSquares

+ [Question](https://leetcode-cn.com/problems/perfect-squares/)：num of Squares which can be added up to n
+ Solution：

```python
from queue import Queue

class Solution:
    def numSquares(self, n: int) -> int:
        around = []
        for i in range(1, n + 1):
            if i ** 2 > n:
                break
            around.append(i ** 2)

        r = 0
        seen = set() 
        q = Queue()
        q.put((0, r))

        while not q.empty():
            cur, step = q.get()
            step += 1

            for a in around:
                a += cur
                if a == n:
                    return step
                if a < n and (a, step) not in seen:
                    seen.add((a, step))
                    q.put((a, step))
                    
        return 0
```

