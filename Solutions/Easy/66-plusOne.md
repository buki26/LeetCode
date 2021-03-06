# 加一

给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

**示例 1**

```
输入: [1,2,3]
输出: [1,2,4]
解释: 输入数组表示数字 123。
```

**示例 2**

```
输入: [4,3,2,1]
输出: [4,3,2,2]
解释: 输入数组表示数字 4321。
```

**我的思路**

开始的思路就是简单的逆序遍历列表，定义一个存放进位的整型，如果需要进位则在下一位把它加上，最后实现出来的代码看着笨笨的，不过扫了一眼题解中别人的答案，看起来和题目的本意不太像，这道题如果把列表转成数字，加一，然后再转回列表，就没意思了不是？所以还是先把我的笨方法记下来吧。。

**我的代码**

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        # 记录进位信息，开始因为要+1，所以初始设置为1
        one = 1
        # 结果放入下面列表，由于for ... in ...这种遍历方法取出值来操作时，并不能原始列表里的值，所以定义一个列表存放结果
        result = []
        # 倒序遍历列表
        for cur in digits[::-1]:
            cur = cur + one
            # 如果加完结果为10，则说明需要进位，当前位设置为0，进位符设置为1
            if cur == 10:
                cur = 0
                one = 1
            # 如果不需要进位，进位符设置为0
            else:
                one = 0
            result.append(cur)
        # 如果列表遍历完，进位符不为0，说明需要加一位了，如[9]->[1, 0]
        if one:
            result.append(one)
        # 返回逆序的列表
        return result[::-1]
```
