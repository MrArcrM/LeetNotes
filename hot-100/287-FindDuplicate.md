

### 287-FindDuplicate

+ [Question](https://leetcode-cn.com/problems/find-the-duplicate-number/)：find duplicate in an array

+ Solution：

  I just copy it. ==Need to review it.==

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        slow,fast,start = 0,0,0
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]
            if slow == fast:
                break
        while start!=slow:
            start = nums[start]
            slow = nums[slow]
        return start        
```

