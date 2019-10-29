# 将有序数组转换为二叉搜索树

将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点   的左右两个子树的高度差的绝对值不超过 1。

**示例**

```
给定有序数组: [-10,-3,0,5,9],

一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：

      0
     / \
   -3   9
   /   /
 -10  5
```

**思路**
仍然应该是树里经典的递归，但我为什么总是没想到呢。。

**代码**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> TreeNode:
        l = 0
        r = len(nums) - 1
        # 递归终止条件
        if l > r:
            return None
        mid = (l + r) // 2
        res = TreeNode(nums[mid])
        res.left = self.sortedArrayToBST(nums[l:mid])
        res.right = self.sortedArrayToBST(nums[mid + 1:r + 1])         # 注意一下这里结尾用的是r+1，因为最后一个是不包含在里面的
        return res
```
