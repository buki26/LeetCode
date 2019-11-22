# 只出现一次的数字

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

**示例 1**
```
输入: [2,2,1]
输出: 1
```

**示例 2**
```
输入: [4,1,2,1,2]
输出: 4
```

**我的思路**

用字典，键为列表里的数字，值是它的计数，最后返回值为1的键。这里涉及到两个不太熟悉的python函数
- setdefault函数，给字典设置默认值，setdefault(a, b)相当于，检查字典里是否有键a，如果有返回a的值，如果没有，创建键a，并把它的值设置为b
- dict和zip函数连用，如下代码所示，实现字典的键值对换

**我的代码**
```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        count = {}
        for cur in nums:
            count.setdefault(cur, 0)
            count[cur] += 1
        reverse_count = dict(zip(count.values(), count.keys()))
        return reverse_count[1]
```
