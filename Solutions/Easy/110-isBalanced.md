# 平衡二叉树

给定一个二叉树，判断它是否是高度平衡的二叉树。

本题中，一棵高度平衡二叉树定义为：

一个二叉树每个节点   的左右两个子树的高度差的绝对值不超过 1。

**示例 1**

```
给定二叉树 [3,9,20,null,null,15,7]

    3
   / \
  9  20
    /  \
   15   7
返回 true 。
```

**示例 2**

```
给定二叉树 [1,2,2,3,3,null,null,4,4]

       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
返回 false 。
```

**我的思路**

终于有点熟悉二叉树递归的套路了，自己写出来啦，不过遇到了 2 个小错误，调试了一会儿，准确的说这题我用到方法是两层递归，第一层递归循环调用自己，用于检查当前节点以及子节点都满足左右子树差不大于 1 这一特点；第二层递归是计算树深度的函数里，用于计算当前节点的深度。

**我的代码**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        if not root:
            return True
        if abs(self.treeDepth(root.left) - self.treeDepth(root.right)) > 1:
            return False
        else:
            '''
            这里开始搞错了，忘记递归调用自己，直接返回True了
            导致的结果是只检查了根节点是符合平衡二叉树特点的，其它子节点不一定满足，比如一个^型的树
            '''
            return self.isBalanced(root.left) and self.isBalanced(root.right)
    def treeDepth(self,root):
        if not root:
            return 0
        elif not root.left and not root.right:
            return 1
        else:
            # 这里计算树深度，不知道为什么总是忘记加1
            return 1 + max(self.treeDepth(root.left),self.treeDepth(root.right))
```
