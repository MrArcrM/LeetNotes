

### 222-CountNodes

+ [Question](https://leetcode-cn.com/problems/count-complete-tree-nodes/)：Count nodes in a completely binary tree

+ My Solution：

  Level-Ordered Traversal, then count the node amount.

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def countNodes(self, root: TreeNode) -> int:
        s = []
        cur = root
        count = 0
        while cur is not None or len(s) > 0:
            while cur is not None:
                s.append(cur)
                cur = cur.left
            cur = s.pop()
            count += 1
            cur = cur.right
        
        return count
```

