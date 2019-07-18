

### 287-FindDuplicate

+ [Question](https://leetcode-cn.com/problems/find-the-duplicate-number/)：find duplicate in an array. Array number is [1...n], there's only one duplicate but may occur for several times.
+ My Solution：`sort`

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        if nums is None or len(nums) == 0: return -1
        
        nums.sort()
        for i in range(1, len(nums)):
            if nums[i] == nums[i-1]:
                return nums[i]
        
        return -1
```

+ Solution-2：use `set()`

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        seen = set()
        for num in nums:
            if num in seen:
                return num
            seen.add(num)
```

