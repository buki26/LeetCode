# 买卖股票的最佳时机

给定一个数组，它的第  i 个元素是一支给定股票第 i 天的价格。

如果你最多只允许完成一笔交易（即买入和卖出一支股票），设计一个算法来计算你所能获取的最大利润。

注意你不能在买入股票前卖出股票。

**示例 1**

```
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。
```

**示例 2**

```
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
```

**我的思路**

想了一下准备用笨办法写一个，也就是暴力循环，两层循环解法超时( ╯□╰ )

**我的代码（超时）**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if len(prices) <= 1:
            return 0
        res = []
        for i in range(len(prices)):
            max_val = 0
            for j in range(i+1, len(prices)):
                if prices[j] - prices[i] > max_val:
                    max_val = prices[j] - prices[i]
            res.append(max_val)
        return max(res)
```

**思路**

看了一个比较聪明的解法，双指针法，第一个指针记录整个列表里的最小值，第二个指针记录当前值与最小值差的最大值，注意保证这个最大值得是大于零的。由于是在一个循环里进行，记录最小值的指针也是从头开始更新的，所以不存在题目说的先卖出后买入的可能。

**代码**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if len(prices) <= 1:
            return 0
        min_p = prices[0]
        max_profit = 0
        for i in range(len(prices)):
            min_p = min(prices[i], min_p)
            max_profit = max(max_profit, prices[i] - min_p)
        return max_profit
```
