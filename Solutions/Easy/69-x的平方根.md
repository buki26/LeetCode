# x 的平方根

实现  int sqrt(int x)  函数。

计算并返回  x  的平方根，其中  x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。

**示例 1**

```
输入: 4
输出: 2
```

**示例 2**

```
输入: 8
输出: 2
说明: 8 的平方根是 2.82842...,
由于返回类型是整数，小数部分将被舍去。
```

**思路**

二分法，注意边界问题。
注意是二分法向下取整，所以返回 left。
另外，注意输入 1 时单独考虑，否则会输出 0
注意循环条件！！

**我的代码**

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 1:
            return x
        left = 0
        right = x
        # 这里要注意，-1很重要，否则会进入死循环
        while left < right - 1:
            mid = left + (right - left) // 2
            square = mid * mid
            if square > x:
                right = mid
            elif square < x:
                left = mid
            else:
                return mid
        return left
```
