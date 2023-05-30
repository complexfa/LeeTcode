### [剑指 Offer 31. 栈的压入、弹出序列](https://leetcode.cn/problems/zhan-de-ya-ru-dan-chu-xu-lie-lcof/)

#### 题目：

输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如，序列 {1,2,3,4,5} 是某栈的压栈序列，序列 {4,5,3,2,1} 是该压栈序列对应的一个弹出序列，但 {4,3,5,1,2} 就不可能是该压栈序列的弹出序列。

```
示例 1：
输入：pushed = [1,2,3,4,5], popped = [4,5,3,2,1]
输出：true
解释：我们可以按以下顺序执行：
push(1), push(2), push(3), push(4), pop() -> 4,
push(5), pop() -> 5, pop() -> 3, pop() -> 2, pop() -> 1
示例 2：
输入：pushed = [1,2,3,4,5], popped = [4,3,5,1,2]
输出：false
解释：1 不能在 2 之前弹出。
```

#### 思路：模拟

建立一个辅助栈，遍历压入栈，当辅助栈不为空且此时顶端元素等于弹出栈元素时，辅助栈弹出顶端元素，并且弹出栈指针向后移。

如果最后辅助栈中仍有元素，说明该弹出序列的不可由该压入栈得到。为空，说明是压入栈的弹出序列。

```
class Solution {
    public boolean validateStackSequences(int[] pushed, int[] popped) {
            Stack<Integer> stack = new Stack<>();
            int j = 0;
            for(int i = 0; i < pushed.length;i++){
                stack.push(pushed[i]);
                while(!stack.isEmpty() && stack.peek() == popped[j])
                {
                    stack.pop();
                    j += 1;
                }
            }
            return stack.isEmpty();
    }
}
```

