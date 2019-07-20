

### 19-RemoveNthFromEnd

+ [Question]()：Remove N<sup>th</sup> node from end in a linked list

+ My Solution：

  use 2 pointers `p1`  `p2`,   `p1` to detect the removed node, `pre` to record the previous node of `p1`

  then if `p1 == head` return `head.next`, else `pre.next = p1.next`, return `head`

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeNthFromEnd(self, head: ListNode, n: int) -> ListNode:
        p2 = head
        for _ in range(n):
            p2 = p2.next
        p1, pre = head, None
        while p2 is not None:
            pre = p1
            p1 = p1.next
            p2 = p2.next
        if p1 == head: return head.next
        pre.next = p1.next
        return head
```

