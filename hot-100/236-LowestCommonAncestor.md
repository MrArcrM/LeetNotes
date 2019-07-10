

### 236-LowestCommonAncestor

+ [Question](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/)：find the lowest common ancestor of two node in a binary tree

+ Solution：

  I just copy it. ==Need to review it.==

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def preOrder(self,root,p,pList):
        if root is None:
            return False
        pList.append(root)
        if root == p:
            return True
        if (self.preOrder(root.left,p,pList)) == True or (self.preOrder(root.right,p,pList)) == True:
            return True
        pList.remove(root)
        return False 
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if root is None or p is None or q is None:
            return None
        pList,qList = [],[]
        self.preOrder(root,p,pList)
        self.preOrder(root,q,qList)
        minList,maxList = (pList,qList) if len(pList)<len(qList) else (qList,pList)
        j = len(minList)-1
        for i in range(len(maxList)-1,-1,-1):
            if maxList[i] == minList[j]:
                return minList[j]
            elif i==j:
                j-=1        
```

