# 爬楼梯

假设你正在爬楼梯。需要 n  阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

**示例 1**

```
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
```

**示例 2**

```
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```

**我的思路**

很经典的题目，迅速用递归调用写了一个，结果 python 竟然超时了，尴尬。。最后学习了别人的代码，通过。

**超时的代码**

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n <= 1:
            return 1
        return self.climbStairs(n - 1) + self.climbStairs(n - 2)
```

**通过的代码**

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        f = [1, 2]
        for i in range(2, n):
            f.append(f[i-1] + f[i-2])
        return f[n-1]

```
