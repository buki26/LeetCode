# 搜索插入位置

给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

**示例 1**

```
输入: [1,3,5,6], 5
输出: 2
```

**示例 2**

```
输入: [1,3,5,6], 2
输出: 1
```

**示例 3**

```
输入: [1,3,5,6], 7
输出: 4
```

**示例 4**

```
输入: [1,3,5,6], 0
输出: 0
```

**我的思路**

经典的二分查找问题，思路没有问题，考虑边界条件有些欠缺，调试了几次，总觉得写出来的代码也有点繁琐。

**我的代码**

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        if target in nums:
            return nums.index(target)
        else:
            l,r = 0,len(nums)-1
            while l < r - 1:
                m = (l + r) // 2
                if nums[m] < target:
                    l = m + 1
                else:
                    r = m - 1
            # 最右
            if nums[l] < target and nums[r] < target:
                return r+1
            # 最左
            elif nums[r] > target and nums[l] > target:
                return l
            else:
                return l+1
```
