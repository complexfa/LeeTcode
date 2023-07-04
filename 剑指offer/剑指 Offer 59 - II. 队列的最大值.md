## [剑指 Offer 59 - II. 队列的最大值](https://leetcode.cn/problems/dui-lie-de-zui-da-zhi-lcof/)

### 题目：

请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。

若队列为空，pop_front 和 max_value 需要返回 -1

```
示例 1：
输入: 
["MaxQueue","push_back","push_back","max_value","pop_front","max_value"]
[[],[1],[2],[],[],[]]
输出: [null,null,null,2,1,2]
示例 2：
输入: 
["MaxQueue","pop_front","max_value"]
[[],[],[]]
输出: [null,-1,-1]
```

### 思路：

```
class MaxQueue {
    int[] queue = new int[10000];
    int begin = 0,end = 0;
    public MaxQueue() {

    }
    
    public int max_value() {
        if(begin == end) return -1;
        int max = queue[begin];
        for(int i = begin;i <= end;i++)
        {
            max = Math.max(queue[i],max);
        }
        return max;
    }
    
    public void push_back(int value) {
        queue[end++] = value;
    }
    
    public int pop_front() {
        if(begin == end) return -1;
        return queue[begin++];
    }
}

/**
 * Your MaxQueue object will be instantiated and called as such:
 * MaxQueue obj = new MaxQueue();
 * int param_1 = obj.max_value();
 * obj.push_back(value);
 * int param_3 = obj.pop_front();
 */
```

