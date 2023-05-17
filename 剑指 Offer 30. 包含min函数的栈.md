

### [剑指 Offer 30. 包含min函数的栈](https://leetcode.cn/problems/bao-han-minhan-shu-de-zhan-lcof/)

#### 题目：

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

#### 思路：辅助栈

通过栈B来记录每加入一个新元素时最小值的情况。

push

| A    | -2   | 0    |      |
| ---- | ---- | ---- | ---- |
| B    | -2   |      |      |

| A    | -2   | 0    | -3   |
| ---- | ---- | ---- | ---- |
| B    | -2   | -3   |      |

pop

| A    | -2   | 0    |      |
| ---- | ---- | ---- | ---- |
| B    | -2   |      |      |

| A    | -2   |      |      |
| ---- | ---- | ---- | ---- |
| B    | -2   |      |      |

| A    |      |      |      |
| ---- | ---- | ---- | ---- |
| B    |      |      |      |

```
class MinStack {
    /** initialize your data structure here. */
    Stack<Integer> A,B;
    public MinStack() {
       A = new Stack();
       B = new Stack();
    }
    
    public void push(int x) {
        A.add(x);
        if(B.empty() || x <= B.peek())
        B.add(x);
    }
    
    public void pop() {
        if(A.pop().equals(B.peek()))
          B.pop();
    }
    
    public int top() {
       return A.peek();
    }
    
    public int min() {
       return B.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.min();
 */
```

