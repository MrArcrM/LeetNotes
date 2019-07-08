

### 113-PathSum

+ [Question](https://leetcode-cn.com/problems/path-sum-ii/)：find all path in a binary tree to add up to a target number
+ My Solution

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def pathSum(self, root: TreeNode, sum: int):
        cur, s, preVal, res = root, [], [], []
        while cur is not None or len(s) > 0:
            while cur is not None:
                s.append((cur, preVal+[cur.val]))
                preVal += [cur.val]
                cur = cur.left

            (cur, li) = s.pop()
            if cur.left is None and cur.right is None and self.sumUp(li) == sum:
                res.append(li)
            preVal = li
            cur = cur.right

        return res

    def sumUp(self, li):
        return sum(li)
```

