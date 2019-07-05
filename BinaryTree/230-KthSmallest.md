

### 230-KthSmallest

+ [Question](https://leetcode-cn.com/problems/kth-smallest-element-in-a-bst/)：find the k<sup>th</sup> smallest num of a BST
+ My Solution：

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def kthSmallest(self, root: TreeNode, k: int) -> int:
        res = []
        s = []
        cur = root
        while len(res) < k and (cur is not None or len(s) > 0):
            while cur is not None:
                s.append(cur)
                cur = cur.left
            cur = s.pop()
            res.append(cur.val)
            cur = cur.right
        
        return res[k-1]        
```

