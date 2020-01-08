# 多数数组

给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数大于  ⌊ n/2 ⌋  的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

**示例 1**

```
输入: [3,2,3]
输出: 3
```

**示例  2**

```
输入: [2,2,1,1,1,2,2]
输出: 2
```

**我最初的思路**

想要直接用暴力法写个答案出来，感觉 python 可以偷个懒，结果就是想法不科学，时间超限了( ╯□╰ )
回想一下，超限原因应该是虽然我用了一层循环，但 python 的 count 方法可能也是一次循环查找的，所以相当于两层循环了。

**时间超限的代码**

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        for x in nums:
            if nums.count(x) > len(nums)/2:
                return x
```

**哈希表法**

思路类似 136 题，用字典计数，这个通过。

**我的代码**

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        counts = {}
        n2 = len(nums) // 2
        for x in nums:
            counts.setdefault(x, 0)
            counts[x] += 1
            if counts[x] > n2:
                return x
```

**很厉害的投票法思路**

然后学习了一个非常厉害的思路，基本思路是，设置一个变量来存放候选值，从头开始遍历并计数，第一个遇到的数字即为候选值，之后遇到的值，如果是候选值则计数+1，不是则计数-1，如果计数为 0 了，则候选值和计数都清零，再从下一位开始设置候选值和计数。

这里由于清零的时候计数器为 0，可以理解为当遍历到计数器清零的点时，遍历过的这一部分数组的众数和非众数数量肯定是相等的，所以后面的数组的众数和整个数组要求得的众数值是一样的，因此清零不影响结果。举一个例子，下面数组中，竖杠的位置为计数器清零的位置：
[7, 7, 5, 7, 5, 1 | 5, 7 | 5, 5, 7, 7 | 7, 7, 7, 7]

**根据以上思路写出的代码**

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        counts = 0
        candidate = None
        for cur in nums:
            if candidate == None:
                candidate = cur
                counts += 1
            elif cur == candidate:
                counts += 1
            else:
                counts -= 1

            if counts == 0:
                candidate = None
        return candidate
```

**投票法更简洁的代码**

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        counts = 0
        candidate = None
        for cur in nums:
            if counts == 0:
                candidate = cur
            counts += (1 if candidate == cur else -1)
        return candidate
```
