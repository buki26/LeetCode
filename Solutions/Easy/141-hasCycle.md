# 环形链表

给定一个链表，判断链表中是否有环。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

**示例 1**

```
输入：head = [3,2,0,-4], pos = 1
输出：true
解释：链表中有一个环，其尾部连接到第二个节点。
```

**示例 2**

```
输入：head = [1,2], pos = 0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点。
```

**示例 3**

```
输入：head = [1], pos = -1
输出：false
解释：链表中没有环。
```

**我的思路**

首先理解题意，不要看示例里的输入，那个输入和代码的输入没有关系，代码的输入就是一个 Listnode 对象。

理解了题目之后，这就是一个普通的链表题了，以前在剑指 offer 里见过的，思路是快慢指针。

**我的代码**

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        pre_node = ListNode(0)
        pre_node.next = head
        slow = pre_node
        fast = pre_node.next

        while fast and fast.next:
            if slow == fast:
                return True

            slow = slow.next
            fast = fast.next.next

        return False
```
