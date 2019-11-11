# 二叉树的最小深度

给定一个二叉树，找出其最小深度。

最小深度是从根节点到最近叶子节点的最短路径上的节点数量。

说明:  叶子节点是指没有子节点的节点。

**示例**

```
给定二叉树  [3,9,20,null,null,15,7],

    3
   / \
   9 20
     / \
    15  7
返回它的最小深度  2.
```

**我的思路**

本来想简单地直接套用最大深度那个题的方法，递归，把 max 换成 min，结果提交出现答案错误的问题，考虑了一下答案错误的情况，发现这个题要考虑的情况稍微多一点，比如一棵树如：

```
    1
     \
      2
```

单纯地把 max 改成 min，会使得代码取深度最小值，得到答案为 1，但实际题目要求到叶子节点的最小深度，2 才是叶子节点，所以分开考虑一个节点只有左节点或者只有右节点的问题。

**我的代码**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def minDepth(self, root: TreeNode) -> int:
        # 当前为空
        if not root:
            return 0
        # 左右都为空
        elif not root.left and not root.right:
            return 1
        # 左为空，右不为空
        elif not root.left and root.right:
            return 1 + self.minDepth(root.right)
        # 左不为空，右为空
        elif root.left and not root.right:
            return 1 + self.minDepth(root.left)
        # 左右都不为空
        else:
            return 1 + min(self.minDepth(root.left),self.minDepth(root.right))
```
