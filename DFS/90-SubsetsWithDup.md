

### 90-SubsetsWithDup

+ [Question](https://leetcode-cn.com/problems/subsets-ii/)：find out all subsets in an array with duplicate
+ My Solution：

```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        if nums is None or len(nums) == 0: return []

        res = []
        def helper(idx, vec):
            if idx >= len(nums):
                vec.sort()
                res.append(vec)
                return
            v = vec.copy()
            v.append(nums[idx])
            helper(idx+1, v)
            helper(idx+1, vec)

        helper(0, [])
        # Remove duplicates from a list of lists
        res.sort()
        res = list(k for k, _ in itertools.groupby(res))

        return res       
```

