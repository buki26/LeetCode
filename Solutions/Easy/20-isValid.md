# 有效的括号

给定一个只包括 '('，')'，'{'，'}'，'['，']'  的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

**示例 1**

```
输入: "()"
输出: true
```

**示例 2**

```
输入: "()[]{}"
输出: true
```

**示例 3**

```
输入: "(]"
输出: false
```

**示例 4**

```
输入: "([)]"
输出: false
```

**示例 5**

```
输入: "{[]}"
输出: true
```

**我的思路**

之前刷题应该见过这道，很容易想到堆栈实现。我想到的方法是，每见到一个左括号，就把它压入栈中，每遇到一个右括号，就弹出一个栈顶元素，并检查遇到的右括号是否和弹出的左括号是成对的，最后检查栈是否为空。
接下来就是寻找 python 里堆栈这个数据结构了，查了一圈结果 python 里竟然没有，可以说很诡异了，好吧，那就用列表实现。

**我的代码**

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        bracket_dict = {')':'(',']':'[','}':'{'}
        for char in s:
            if char in bracket_dict:
                # 注意这里存在一个边界问题，否则会在空栈中做pop操作
                if stack:
                    top = stack.pop()
                else:
                    return False
                if top!=bracket_dict[char]:
                    return False
            else:
                stack.append(char)

        if stack==[]:
            return True
        else:
            return False
```
