# 对称二叉树

给定一个二叉树，检查它是否是镜像对称的。

```
例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

    1
   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

    1
   / \
  2   2
   \   \
   3    3
```

**思路**

还是递归，明明和 100 题是类似的思路，但不知道为什么，上一个题想到了，这个题自己就没想到方法，看来还是对递归不太熟，需要再巩固一下。

**代码**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSymmetric(self, root: TreeNode) -> bool:
        if not root:
            return True
        return self.isMirror(root.left,root.right)

    def isMirror(self, p, q):
        if not p and not q:
            return True
        if not p and q:
            return False
        if p and not q:
            return False
        # 以下说明p和q都不为空
        if p.val != q.val:
            return False
        l = self.isMirror(p.left, q.right)
        r = self.isMirror(p.right, q.left)
        return l and r
```
