### 141-HasCycle

+ [Question](https://leetcode-cn.com/problems/linked-list-cycle/)：if a linkedlist has cycle
+ Solution：

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        pFast = head
        pSlow = head
        while pFast is not None and pSlow is not None:
            if pFast.next is None: return False
            pFast = pFast.next.next
            pSlow = pSlow.next
            if pFast == pSlow:
                return True
        return False      
```

+ Related：

  🏷 [`142-DetectCycle`](./142-DetectCycle.md)

  