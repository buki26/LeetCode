# 两数之和

给定一个整数数组 nums  和一个目标值 target，请你在该数组中找出和为目标值的那   两个   整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

**示例**

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

**思路**
直观理解题目的含义，即对于索引 i，target-nums[i]也在 nums 列表中。
可以通过 列表.index（元素值） 来获取元素的索引，这里需要注意的一点是，题目要求不能重复利用，所以要保证两个索引不同。

**代码**

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        i = 0
        for i in range(len(nums)):
            if target-nums[i] in nums and nums.index(target-nums[i])!=i:
                j = nums.index(target-nums[i])
                return [i,j]
```
