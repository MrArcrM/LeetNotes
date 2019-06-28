

###  142-DetectCycle

+ [Question](https://leetcode-cn.com/problems/linked-list-cycle-ii/)：Find the 'in-cycle' node of a linkedlist, return `null` if it doesn't exsit

+ Analysis：

  [How to find the 'in-cycle' node](https://leetcode-cn.com/submissions/detail/21412481/)：when pFast meet pSlow, set pSlow = pHead, then pFast, pSlow move step by step. When they meet again at pNode, pNode is the 'in-cycle' node.

  `Demonstration`：

  ```
  设整个链表长度为L，环长度为R，且距离具有方向性，
  例如CB是C点到B点的距离，BC是B点到C点的距离，CB!=BC。
  当证明有环时，fast和slow到了B点，则此时：
  slow走的距离：AC+CB
  fast走的距离：AC+k*R+CB(k=0,1,2...)
  由于fast每次走2个节点，slow每次走1个节点，所以：
  2(AC+CB) = AC+k*R+CB
  AC+CB = k*R
  AC+CB = (k-1)*R+R
  AC = (k-1)*R+R-CB
  AC = (k-1)*R+BC
  从最终的表达式可以看出来，AC的距离等于绕环若干圈后再加上BC的距离，
  也就是说慢指针从A点出发以速度1前进、快指针从B点出发以速度1前进，
  则慢指针到C点时，快指针也必然到了。
  ```

+ My Solution：

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head is None or head.next is None: return None
        fast = slow = head
        while True:
            if fast is None: return None
            fast = fast.next
            if fast is None: return None
            fast = fast.next

            slow = slow.next
            if fast == slow: break
        slow = head
        while fast != slow:
            fast = fast.next
            slow = slow.next

        return slow        
```

+ Related：

  [`141-HasCycle`](./141-HasCycle.md)

