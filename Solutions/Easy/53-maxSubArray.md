# 最大子序和

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

**示例**

```
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

**思路**

非常经典的动态规划题目，之前用 c++刷剑指 offer 的时候遇到过，看了一下以前的笔记，改写成了 python 版本。

**我的代码**

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        if len(nums) == 0:
            return 0
        # 不能用0初始化，以防数组中都为负值
        max_sum = nums[0]
        temp_sum = nums[0]
        # 循环从1开始，因为0在初始化时已经考虑了
        for i in range(1,len(nums)):
            # 和小于0的时候抛弃之前的一串
            temp_sum = temp_sum + nums[i] if temp_sum > 0 else nums[i]
            # 更新最大值
            max_sum = max(max_sum,temp_sum)
        return max_sum
```
