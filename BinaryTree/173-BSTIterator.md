

### 173-BSTIterator

+ [Question](https://leetcode-cn.com/problems/binary-search-tree-iterator/)：implement `next()`、`hasNext()` method of a BST with O(1) Time and O(h) Space
+ My Solution：

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class BSTIterator:

    def __init__(self, root: TreeNode):
        self.root = root
        self.node = root
        while self.node is not None and self.node.left is not None:
            self.node = self.node.left

    def next(self) -> int:
        """
        @return the next smallest number
        """
        res = self.node.val
        if self.node == self.root:
            self.root = self.node.right
        elif self.node.right is not None:
            p = self.root
            while p.left != self.node:
                p = p.left
            p.left = self.node.right
        else:
            p = self.root
            while p.left != self.node:
                p = p.left
            p.left = None
        p = self.root
        while p is not None and p.left is not None:
            p = p.left
        self.node = p
        return res

    def hasNext(self) -> bool:
        """
        @return whether we have a next smallest number
        """
        return self.root is not None
        


# Your BSTIterator object will be instantiated and called as such:
# obj = BSTIterator(root)
# param_1 = obj.next()
# param_2 = obj.hasNext()
```

