

### 380-RandomizedSet

+ [Question](https://leetcode-cn.com/problems/insert-delete-getrandom-o1/)：use a data structure to implement `insert(val)`、`remove(val)`、`getRandom()` in O(1) Time
+ Analysis：use `OrderedDict`
+ My Solution：⏰ 30''

```python
from collections import OrderedDict
import random

class RandomizedSet:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.od = OrderedDict()

    def insert(self, val: int) -> bool:
        """
        Inserts a value to the set. Returns true if the set did not already contain the specified element.
        """
        if val not in self.od:
            self.od[val] = val
            return True
        return False

    def remove(self, val: int) -> bool:
        """
        Removes a value from the set. Returns true if the set contained the specified element.
        """
        if val in self.od:
            self.od.move_to_end(val)
            self.od.popitem(last=True)
            return True
        return False

    def getRandom(self) -> int:
        """
        Get a random element from the set.
        """
        return random.choice(list(self.od.values()))
        


# Your RandomizedSet object will be instantiated and called as such:
# obj = RandomizedSet()
# param_1 = obj.insert(val)
# param_2 = obj.remove(val)
# param_3 = obj.getRandom()
```

