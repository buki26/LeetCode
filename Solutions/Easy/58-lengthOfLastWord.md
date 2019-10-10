# 最后一个单词的长度

给定一个仅包含大小写字母和空格  ' '  的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。

说明：一个单词是指由字母组成，但不包含任何空格的字符串。

**示例**

```
输入: "Hello World"
输出: 5
```

**我的思路**

开始的想法很简单，根据给出的示例，要做的就是逆序遍历字符串，定义计数器记录字符个数，遇到空格则跳出循环，字符串遍历完自然也就会结束计数，最后返回计数结果。

但是这样做在调试过程中遇到了一个没考虑的情况，即对于输入"a "，我的代码在逆序遍历遇到空格时返回，也就时返回结果为 0，可是正确答案应该是 1，因此在循环前面添加了去除字符串前后的空格，调试通过。

**我的代码**

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        # 去除字符串前后空格
        s = s.strip()
        count = 0
        for i in list(s)[::-1]:
            if i==' ':
                break
            count+=1
        return count
```

**更简单的方法**

还是对 python 不熟悉，自己肿么想不到，用 split 分割，然后取最后一个啊，另外，上面用到的 strip 是去除字符串前后的空格，这里可以用 rstrip 去除字符串后面的空格。

**更简洁的代码**

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        return len(s.rstrip().split(' ')[-1])
```
