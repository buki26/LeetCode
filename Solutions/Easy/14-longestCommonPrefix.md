# 最长公共前缀

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串  ""。

**示例  1**

```
输入: ["flower","flow","flight"]
输出: "fl"
```

**示例  2**

```
输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。
```

**说明**
所有输入只包含小写字母  a-z 。

**我的思路**
很笨的方法，定义指针，从第一个字母开始挨个检查，容易想到但是实现起来边界问题还是很麻烦。

**我的代码**

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        res = ""
        i = 0
        # 如果输入是空列表或者第一个字符串为空
        if len(strs)==0 or len(strs[0])==0:
            return res
        # 取出第一个字符串的第一个字母
        temp = strs[0][0]
        while True:
            # 对于列表中的每一个字符串，检查是否等于第一个字符串的对应值
            for cur in strs:
                # 如果当前字符串已经没有第i位字母了
                if len(cur) <= i:
                    return res
                # 或者第i位字母与取出的temp不等
                if cur[i]!=temp:
                    return res
            # 这次循环结束，并且没有返回，说明temp是每个字符串都存在的前缀，把它加入结果
            res = res + temp
            # 指针后移，并取第一个字符串的下一位作为temp，注意后移之后要检查一下第一个字符串的长度，否侧容易出现数组越界的错误
            i = i + 1
            if len(strs[0]) <= i:
                return res
            temp = strs[0][i]
        return res
```

**别人的思路**
zip 函数了解一下,可以理解为一个打包函数，zip(\*)官方解释是反向打包，也就是解压操作
比如给 zip(\*)函数传递一个存放字符串的列表，这个函数将字符串中的对应位元素打包成元组。
以 strs=["flower","flow","flight"]为例：
list(zip(\*strs))的输出为:
[('f', 'f', 'f'), ('l', 'l', 'l'), ('o', 'o', 'i'), ('w', 'w', 'g')]
ps:因为 zip(\*)生成的是迭代器，所以打印加上了 list

**别人的代码**

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        L = zip(*strs)
        # [('f', 'f', 'f'), ('l', 'l', 'l'), ('o', 'o', 'i'), ('w', 'w', 'g')]

        r = [len(set(c)) == 1 for c in L] + [False]
        # set()去重
        # len(set(c)) == 1 检查去除重复元素后的元组的长度是否等于1，也就是检查对应位是否相等
        # 在列表的最后添了一位False，是因为后面需要查找第一个False的下标，不加的话有可能会因为没有False而报错

        if strs != []:
            s = r.index(False)  # 查找第一个False的下标
            return strs[0][0:s]  # 列表查找+切片
        else:
            return ''
```
