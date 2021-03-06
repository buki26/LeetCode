# Excel 表列序号

给定一个正整数，返回它在 Excel 表中相对应的列名称。

例如，

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB
    ...

**示例 1**

```
输入: 1
输出: "A"
```

**示例  2**

```
输入: 28
输出: "AB"
```

**示例  3**

```
输入: 701
输出: "ZY"
```

**思路**

正常的思路应该是 10 进制转 26 进制，自己写了半天，复杂且没成功，最终还是参照了别人的思路。

10 进制转 26 进制，可以参照 10 进制转 2 进制去理解，用 n 除以 26，得到结果和余数，循环去做。另外存在的问题是，当 n 为 26 的整数倍时，比如 n=26，这时得到结果是 1，余数为 0，而实际上我们想要返回的结果应该是 Z，所以当余数为 0 时，像前借一位，结果设置为 0，余数为 26，这样就可以和 ASCII 码里的字母对应了。

**代码**

```python
class Solution:
    def convertToTitle(self, n: int) -> str:
        res = ""
        while n:
            n, y = divmod(n, 26)
            if y == 0:
                n -= 1
                y = 26
            res = chr(y + 64) + res
        return res

```
