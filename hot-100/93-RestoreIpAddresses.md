

### 93-RestoreIpAddresses

+ [Question](https://leetcode-cn.com/problems/restore-ip-addresses/)：
+ Solution：

```python
class Solution:
    def restoreIpAddresses(self, s: str) -> List[str]:
        n = len(s)
        res = []
		# 判读是否满足ip的条件
        def helper(tmp):
            if not tmp or (tmp[0] == "0" and len(tmp) > 1) or int(tmp) > 255:
                return False
            return True
		# 三个循环,把数字分成四份
        for i in range(3):
            for j in range(i + 1, i + 4):
                for k in range(j + 1, j + 4):
                    if i < n and j < n and k < n:
                        tmp1 = s[:i + 1]
                        tmp2 = s[i + 1:j + 1]
                        tmp3 = s[j + 1:k + 1]
                        tmp4 = s[k + 1:]
                        # print(tmp1, tmp2, tmp3, tmp4)

                        if all(map(helper, [tmp1, tmp2, tmp3, tmp4])):
                            res.append(tmp1 + "." + tmp2 + "." + tmp3 + "." + tmp4)
        return res

```

