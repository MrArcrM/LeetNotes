

### 18-FourSum

+ [Question](https://leetcode-cn.com/problems/4sum/)：find all four-num tuple to add up to target
+ My Solution：

```python
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        if nums is None or len(nums) < 4: return []
        
        res = []
        nums.sort()
        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            for j in range(i+1, len(nums)):
                if j > i+1 and nums[j] == nums[j-1]:
                    continue
                p1, p2 = j+1, len(nums)-1
                while p1 < p2:
                    sums = nums[i] + nums[j] + nums[p1] + nums[p2]
                    if sums == target:
                        res.append([nums[i], nums[j], nums[p1], nums[p2]])
                        p1 += 1
                        p2 -= 1
                        while p1 < p2 and nums[p1] == nums[p1-1]:
                            p1 += 1
                        while p1 < p2 and nums[p2] == nums[p2+1]:
                            p2 -= 1
                    elif sums > target:
                        p2 -= 1
                        while p1 < p2 and nums[p2] == nums[p2+1]:
                            p2 -= 1
                    else:
                        p1 += 1
                        while p1 < p2 and nums[p1] == nums[p1-1]:
                            p1 += 1
        
        return res
        
```



