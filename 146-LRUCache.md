

### 146-LRUCache

+ [Question]()：use 'LeastRecentlyUsed' rule to implement method `init()`、`get()`O(1) and `put()`O(1)

+ Analysis：

  Use data structure named `OrderedDict`. By contrast to regular dict, the order the items are inserted is remembered by OrderedDict.

+ Solution：

```python
from collections import OrderedDict

class LRUCache:

    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.capacity = capacity
        self.cache = OrderedDict()


    def get(self, key):
        """
        :type key: int
        :rtype: int
        """
        if key not in self.cache:
            return -1
        self.cache.move_to_end(key)
        return self.cache[key]


    def put(self, key, value):
        """
        :type key: int
        :type value: int
        :rtype: None
        """
        if key in self.cache:
            self.cache.move_to_end(key)
        self.cache[key] = value
        if len(self.cache) > self.capacity:
            self.cache.popitem(last=False)
        


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```

+ Related：

  OrderedDict is implemented by Doubly Linked List. For detail, [146-official solution-method2](https://leetcode-cn.com/problems/lru-cache/solution/lru-huan-cun-ji-zhi-by-leetcode/)

