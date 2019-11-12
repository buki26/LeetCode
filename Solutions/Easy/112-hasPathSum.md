# 路径之和

给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。

说明:  叶子节点是指没有子节点的节点。

**示例**

```
给定如下二叉树，以及目标和 sum = 22，

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
返回 true, 因为存在目标和为 22 的根节点到叶子节点的路径 5->4->11->2。
```

**思路**

递归的基本思路是对哒，但是后面有一个很重要的小地方没想到。两个边界条件分别是，根节点为空及只有一个节点的情况，然后递归调用看子树是否符合，由于任一条路的路径和为 sum 都可以返回 True，所以递归调用左右子树中间用的是 or 而不是 and。唯一没想到的一小点是，递归调用子树的时候，直接把 target 值设置为 sum-root.val,也就是判断子树的和是否等于目标值减去当前节点的值。

**代码**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def hasPathSum(self, root: TreeNode, sum: int) -> bool:
        if not root:
            return False
        elif not root.left and not root.right:
            return sum==root.val
        else:
            return self.hasPathSum(root.left,sum-root.val) or self.hasPathSum(root.right,sum-root.val)
```
