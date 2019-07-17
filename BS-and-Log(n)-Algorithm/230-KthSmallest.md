

### 230-KthSmallest

+ [Question](https://leetcode-cn.com/problems/kth-smallest-element-in-a-bst/)：find the k<sup>th</sup> smallest elements in a BST

+ My Solution：

  InOrder Traversal, then return arr[k-1]

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        if root is None or k <= 0: return -1
        s, arr = [], []
        cur = root
        while cur is not None or len(s) > 0:
            while cur is not None:
                s.append(cur)
                cur = cur.left
            cur = s.pop()
            arr.append(cur.val)
            cur = cur.right
        
        return arr[k-1]
            
        
```

