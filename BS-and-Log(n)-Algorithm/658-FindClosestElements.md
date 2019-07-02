

### 658-FindClosestElements

+ [Question](https://leetcode-cn.com/problems/find-k-closest-elements/)：use 2 pointers `pLeft` and `pRight`

+ My Solution：

  binarySearch：return idx if arr[idx] == x or idx if arr[idx] is the first smaller number than x

```python
class Solution:
    def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
        n = len(arr)
        if x < arr[0]: return arr[0:k]
        elif x > arr[-1]: return arr[n-k:n]
        
        pLeft = self.binarySearch(arr, x)
        pRight = pLeft + 1
        while k > 0 and pLeft >= 0 and pRight < n:
            if x - arr[pLeft] <= arr[pRight] - x:
                pLeft -= 1
                k -= 1
            else:
                pRight += 1
                k -= 1
        if k > 0:
            if pLeft >= 0: pLeft -= k
            if pRight < n: pRight += k
        return arr[pLeft+1:pRight]        

    def binarySearch(self, arr, x):
        pStart = 0
        pEnd = len(arr) - 1
        while pStart + 1 < pEnd:
            pMid = int((pStart + pEnd) / 2)
            if arr[pMid] == x: return pMid
            elif arr[pMid] > x: pEnd = pMid - 1
            else: pStart = pMid + 1
        return pStart
```

