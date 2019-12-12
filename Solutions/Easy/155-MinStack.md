# 最小栈

设计一个支持 push，pop，top 操作，并能在常数时间内检索到最小元素的栈。

push(x) -- 将元素 x 推入栈中。
pop() -- 删除栈顶的元素。
top() -- 获取栈顶元素。
getMin() -- 检索栈中的最小元素。

**示例**

```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); --> 返回 -3.
minStack.pop();
minStack.top(); --> 返回 0.
minStack.getMin(); --> 返回 -2.
```

**我的思路**

用列表实现，唯一需要注意的事就是在类里面定义和调用成员变量记得加 self.

然后突然想到一句话就是用 python 刷某些题简直就是耍流氓 O(∩_∩)O

**我的代码**

```python
class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.stack_data = []

    def push(self, x: int) -> None:
        self.stack_data.append(x)

    def pop(self) -> None:
        del self.stack_data[-1]

    def top(self) -> int:
        return self.stack_data[-1]

    def getMin(self) -> int:
        return min(self.stack_data)


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(x)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```
