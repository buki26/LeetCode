# 杨辉三角

给定一个非负整数  numRows，生成杨辉三角的前  numRows  行。

在杨辉三角中，每个数是它左上方和右上方的数的和。

**示例**

```
输入: 5
输出:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

**思路**

应该是动态规划，自己往递归上靠了好久都没成功，最后还是看了别人的代码，需要注意一下边界问题。

**代码**

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        # 注意：[0]*2得到的是[2, 2]
        # 创建符合输入行数的杨辉三角的形状，用0填充
        dp = [[0]*n for n in range(1,numRows+1)]
        # 每一行的第1个和最后一个填1
        for i in range(numRows):
            dp[i][0] = 1
            dp[i][-1] = 1
        # i, j分别为行和列，注意边界，否则会超限
        for i in range(numRows):
            for j in range(i+1):
                # 当前为0时才计算，目的是刨去边上的1
                if dp[i][j] == 0:
                    dp[i][j] = dp[i-1][j-1] + dp[i-1][j]
        return dp
```
