

### 372-SuperPow

+ [Question](https://leetcode-cn.com/problems/super-pow/)：a<sup>b</sup> mod c，b is a big integer array，a、c is integer

+ Analysis：

  `formula-1`：(x<sup>a</sup> * y<sup>b</sup>) % c = ((x<sup>a</sup> % c) * (y<sup>b</sup> % c)) % c 

  `formula-2`：x<sup>a</sup> % c = (x<sup>a/2</sup> % c * x<sup>a/2</sup> % c) % c，a is odd

  `formula-3`：x<sup>a</sup> % c = (x<sup>a/2</sup> % c * x<sup>a/2</sup> % c * x) % c，a is even

+ Solution：

```python
class Solution:
    def superPow(self, a: int, b: List[int]) -> int:
      	'''
      		(x^a * y^b) % c = ((x^a % c) * (y^b % c)) % c 
      	'''
        modNum = 1337
        res = 1
        for i in range(len(b)):
            res = (self.getMod(res, 10, modNum) * self.getMod(a, b[i], modNum)) % modNum
        return res

    def getMod(self, base, expo, modNum):
        '''
            a is odd: x^a % c = (x^a/2 % c * x^a/2 % c) % c
                even: x^a % c = (x^a/2 % c * x^a/2 % c * x) % c
        '''
        if expo == 0: return 1 % modNum
        if expo == 1: return base % modNum
        product = self.getMod(base, int(expo/2), modNum) \
        						* self.getMod(base, int(expo/2), modNum)
        if expo % 2 != 0: product *= base
        return product % modNum        
```



