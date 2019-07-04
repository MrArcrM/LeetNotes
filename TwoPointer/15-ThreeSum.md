

### 15-ThreeSum

+ [Question](https://leetcode-cn.com/problems/3sum/)：find all three tuples which is added to be 0 in an array

+ Analysis：

  fix a number `nums[i]`, then use 2 pointers to find the match pairs `nums[first]=0`, `nums[last]=n-1`：

  + when `nums[i]>0` , continue to `nums[i+1]`, because `nums[i] > nums[first] > nums[last]`, it's impossible to add up to 0
  + when `i>0` and `nums[i]==nums[i-1]`, continue to `nums[i+1]`, because `nums[i]` has been calculated as `num[i-1]`
  + when `nums[first] == nums[first-1]` or `nums[last]==nums[last+1]`, skip it.

+ Solution：

  O(n<sup>2</sup>) Time

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        if nums is None or len(nums) == 0: return []
        res = []
        n = len(nums)
        nums.sort()
        for i in range(n-2):
            if nums[i] > 0: continue  # because i > first > last
            if i > 0 and nums[i] == nums[i-1]: continue  # skip
            first, last = i+1, n-1
            while first < last:
                sum = nums[i] + nums[first] + nums[last]
                if sum < 0:
                    first += 1
                    while first < last and nums[first] == nums[first-1]: first += 1
                elif sum > 0:
                    last -= 1
                    while first < last and nums[last] == nums[last+1]: last -= 1
                else:
                    res.append([nums[i], nums[first], nums[last]])
                    first += 1
                    while first < last and nums[first] == nums[first - 1]: first += 1
                    last -= 1
                    while first < last and nums[last] == nums[last + 1]: last -= 1

        return res        
```

