# 验证回文串

给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。

**示例 1**

```
输入: "A man, a plan, a canal: Panama"
输出: true
```

**示例 2**

```
输入: "race a car"
输出: false
```

**我的思路**

思想其实非常简单，只是有些 python 的函数不太熟悉，需要查一下。基本思路就是把字符串只保留数字和字母（去掉空格和符号等），全部转成小写，然后看它和逆序的它是否相等。

**我的代码**

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        if s == "":
            return True
        # isalnum判断是否是数字和字母，filter将s所有字符应用于isalnum并保留符合条件的
        # 由于filter返回迭代器，所以转为list，并用"".join把list转为string
        # lower转为全小写
        s = "".join(list(filter(str.isalnum, s))).lower()
        return s[::-1]==s
```

**一点经验**

- 当某个函数返回迭代器时，可以用 list 把它转为列表，如果应该是字符串形式，那就加上"".join 来把列表转为字符串。
- 列表或字符串的逆序：s[::-1]
