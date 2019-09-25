# 实现 strStr()

实现 strStr()函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置(从 0 开始)。如果不存在，则返回-1。

**示例 1**

```
输入: haystack = "hello", needle = "ll"
输出: 2
```

**示例 2**

```
输入: haystack = "aaaaa", needle = "bba"
输出: -1
```

**说明**

当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 needle 是空字符串时我们应当返回 0。这与 C 语言的 strstr()以及 Java 的 indexOf()定义相符。

**我的思路**

这个问题对于 python 而言好像有点没意义，直接判断 needle 是否存在于 haystack 中，如果存在，返回索引，否则返回-1.

**我的代码**

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if needle == "":
            return 0
        if needle in haystack:
            return haystack.index(needle)
        else:
            return -1
```
