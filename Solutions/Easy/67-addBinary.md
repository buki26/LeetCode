# 二进制求和

给定两个二进制字符串，返回他们的和（用二进制表示）。

输入为非空字符串且只包含数字  1  和  0。

**示例  1**

```
输入: a = "11", b = "1"
输出: "100"
```

**示例  2**

```
输入: a = "1010", b = "1011"
输出: "10101"
```

**我的思路**

超级笨的办法，类似 66 题，很多 if else 判断，但是在评论里也没有找到非常好的方法实现。

**我的代码**

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        # 把输入逆序，方便对齐
        a = a[::-1]
        b = b[::-1]
        digits = 0
        i = 0
        result = ""
        while i < len(a) or i < len(b):
            # 如果a或b已经遍历完了，防止溢出
            if i >= len(a):
                cur = int(b[i]) + digits
            elif i >= len(b):
                cur = int(a[i]) + digits
            else:
                cur = int(a[i]) + int(b[i]) + digits
            # 如果当前数字为2，进一位当前改为0
            if cur == 2:
                cur = 0
                digits = 1
            # 如果当前数字为3，进一位，当前为1
            elif cur == 3:
                cur = 1
                digits = 1
            # 否则不进位
            else:
                digits = 0
            result = result + str(cur)
            i += 1
        # 如果遍历结束，进位不为0，则增加一位
        if digits:
            result = result + str(digits)
        # 注意要返回的结果为逆序
        return result[::-1]
```

**内置函数方法**

虽然这不是这道题目的本意，但在实际中要实现二进制位相加一定是用内置函数实现的，所以记录一下 bin 函数

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        # 把a和b从str转成int，注意是二进制，用bin实现二进制相加
        # 后面取[2:]的原因是输出二进制输出前两位是0b，如0b101
        return bin(int(a, 2) + int(b, 2))[2:]
```
