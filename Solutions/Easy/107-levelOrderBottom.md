# 二叉树的层次遍历 II

给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）

```
例如：
给定二叉树 [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其自底向上的层次遍历为：

[
  [15,7],
  [9,20],
  [3]
]
```

**思路**

这个题目自己没有想到，思想还是递归，参考了讨论区一个人的代码。

**代码**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
        res = []
        # cur存放当前要遍历的节点
        cur = [root]
        while cur:
            # cur_layer_val存放当前层的值
            cur_layer_val = []
            # next_layer_node从左到右存放下一层的节点
            next_layer_node = []
            for node in cur:
                # 确定当前节点不为空
                if node:
                    cur_layer_val.append(node.val)
                    next_layer_node.extend([node.left,node.right])
            # 确定存放当前层节点值的列表不为空，则插入的结果列表的第一位
            if cur_layer_val:
                res.insert(0,cur_layer_val)
            # 将存放下一层节点的列表置为cur
            cur = next_layer_node
        return res
```
