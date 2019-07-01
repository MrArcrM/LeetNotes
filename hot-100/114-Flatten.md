



### 114-Flatten

+ [Question](https://leetcode-cn.com/problems/flatten-binary-tree-to-linked-list/)：Flatten a binary tree

+ My Solution：

  Something like `Clue Binary Tree`，for detail：[LeetCode94-Official Solution-Method3](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/solution/er-cha-shu-de-zhong-xu-bian-li-by-leetcode/)

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def flatten(self, root: TreeNode) -> None:
        """
        Do not return anything, modify root in-place instead.
        """
        cur = root
        while cur is not None:
            if cur.left is not None:
                last = cur.left
                while last.right is not None:
                    last = last.right
                last.right = cur.right
                cur.right = cur.left
                cur.left = None
            cur = cur.right
```

