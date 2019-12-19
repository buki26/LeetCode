# 两数之和 II - 输入有序数组

给定一个已按照升序排列   的有序数组，找到两个数使得它们相加之和等于目标数。

函数应该返回这两个下标值 index1 和 index2，其中 index1  必须小于  index2。

说明:

返回的下标值（index1 和 index2）不是从零开始的。
你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。
**示例**

```
输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。
```

**错误的思路和代码**

首先贴一个我尝试失败了的思路和代码。这个思路是想一次循环，找和当前值之和等于 target 的，并且找到的那个值的 index 还不能和当前值的 index 相等，符合这样条件的返回，但是这个思路没有办法处理形如[0,0,3,4]，target=0 的情况.

因为对 list[0,0,0,0]求 list.index(0)只返回 0，也就是说只返回第一个 0 的位置，后面的被无视了。

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        for i in range(len(numbers)):
            if target-numbers[i] in numbers and numbers.index(target-numbers[i]) > i:
                return [i+1, numbers.index(target-numbers[i])+1]
        return []
```

**思路**

所以正常的思路应该是双指针法，一个指头，另一个指尾，判断它们的和，决定是第一个指针后移还是第二个指针前移。

**正确代码**

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l = 0
        r = len(numbers)-1
        while l < r:
            if numbers[l] + numbers[r] == target:
                return [l+1, r+1]
            elif numbers[l] + numbers[r] < target:
                l = l + 1
            else:
                r = r - 1
        return [-1, -1]
```
