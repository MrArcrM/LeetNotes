

### 208-Trie

+ [Question](https://leetcode-cn.com/problems/implement-trie-prefix-tree/)：implement method `init`、`search`、`startsWith` of a [Trie](https://www.geeksforgeeks.org/trie-insert-and-search/)
+ Solution：

```python
class TrieNode:
    def __init__(self):
        self.children = [None] * 26
        self.isEndOfWord = False

class Trie:
    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.root = self.getNode()

    def insert(self, word: str) -> None:
        """
        Inserts a word into the trie.
        """
        if self.search(word): return
        pCrawl = self.root
        for level in range(len(word)):
            index = self.charToIndex(word[level])
            if not pCrawl.children[index]:
                pCrawl.children[index] = self.getNode()
            pCrawl = pCrawl.children[index]
        pCrawl.isEndOfWord = True


    def search(self, word: str) -> bool:
        """
        Returns if the word is in the trie.
        """
        node = self.getEndNode(word)
        return node is not None and node.isEndOfWord

    def startsWith(self, prefix: str) -> bool:
        """
        Returns if there is any word in the trie that starts with the given prefix.
        """
        node = self.getEndNode(prefix)
        return node is not None

    def getNode(self):
        return TrieNode()

    def charToIndex(self, ch):
        return ord(ch) - ord('a')

    def getEndNode(self, word) -> TrieNode:
        pCrawl = self.root
        for level in range(len(word)):
            index = self.charToIndex(word[level])
            if not pCrawl.children[index]: return None
            pCrawl = pCrawl.children[index]
        return pCrawl
        


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```

