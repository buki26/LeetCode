# 合并两个有序数组

给定两个有序整数数组  nums1 和 nums2，将 nums2 合并到  nums1  中，使得  num1 成为一个有序数组。

说明:

初始化  nums1 和 nums2 的元素数量分别为  m 和 n。
你可以假设  nums1  有足够的空间（空间大小大于或等于  m + n）来保存 nums2 中的元素。
**示例**

```
输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

输出: [1,2,2,3,5,6]
```

**思路**

自己的想法不知道为什么，开始理解成必须在原地执行，然后把思路搞的很复杂，最后还是看了别人的代码，两种思路，第一种先相加后排序(个人感觉仍然不是题目的本意)，第二种两个列表各自一个指针，不过还是要先把其中一个列表复制一份。

注意：复制时要加[:],否则相当于引用。

**代码 1**

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        nums1[:] = sorted(nums1[:m] + nums2[:])
        return nums1
```

**代码 2**

```python
'''
按照第二种思路自己写的代码，感觉也毫无技术含量
时间还慢了30ms，不知道图啥。。
唯一需要记住的，列表拷贝的问题。
'''
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        # 注意这里不要直接给数组0赋值，直接赋值为浅拷贝
        nums0 = nums1[:m]
        i = 0
        j = 0
        q = 0
        if m == 0 and n == 0:
            return nums1
        while i < m and j < n:
            if nums0[i] <= nums2[j]:
                nums1[q] = nums0[i]
                i += 1
            else:
                nums1[q] = nums2[j]
                j += 1
            q += 1
        if i >= m:
            while j < n:
                nums1[q] = nums2[j]
                j += 1
                q += 1
        elif j >= n:
            while i < m:
                nums1[q] = nums0[i]
                i += 1
                q += 1
        return nums1
```
