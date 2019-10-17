# 删除排序链表中的重复元素

给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。

**示例  1**

```
输入: 1->1->2
输出: 1->2
```

**示例  2**

```
输入: 1->1->2->3->3
输出: 1->2->3
```

**我的思路**

两个指针，一个指向当前节点，一个指向上一个节点，判断它两的值，值一样则删除当前节点，不一样则两个指针都后移，循环结束条件是当前节点为空（这时不能取 next 了），注意开始先判断边界条件，输入为空链表的情况。

**我的代码**

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        if not head:
            return None
        # 定义头节点，接在输入前，用于返回
        pre_node = ListNode(0)
        pre_node.next = head
        # 前一个指针pre，初始指向头节点后的第一个节点
        pre = pre_node.next
        # 当前节点cur，初始指向第二个节点，即第一个节点后的一个节点，如果只有一个节点的链表，那cur初始为空，不进入下面循环
        cur = pre.next
        while cur:
            # 删除cur节点
            if pre.val == cur.val:
                pre.next = cur.next
                cur = pre.next
            # 两个指针后移
            else:
                pre = pre.next
                cur = cur.next
        return pre_node.next
```
