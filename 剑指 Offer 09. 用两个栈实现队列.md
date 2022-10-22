#### [剑指 Offer 09. 用两个栈实现队列](https://leetcode.cn/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

#### 用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 `appendTail` 和 `deleteHead` ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，`deleteHead` 操作返回 -1 )

队列为先入先出，栈为先入后出。

B实现A的倒序排列

增加元素即在A中栈顶增加

删除元素即将A倒序再删除栈顶元素，即删除B中的栈顶元素

如果A本身为空则无元素，返回-1；

如果A本身有元素，则循环输入到B中，然后再从B中输出栈顶元素

如果B本身有元素，那么直接输出栈顶元素

（这种情况一开始没懂，当栈b不是空时，会直接返回栈b的栈顶元素也就是队首元素，直到栈b为空，再次把栈a中的元素倒序入b。

那么假设是12345

A：12345

B：54321

新加元素6，那么A就会改变

A:6，如果此时没有把B中的先删，那么就会得到6，而不是1

所以得先将B中的先删，才能得到队首元素，直到空了，再把A中的倒序入B）

```
class CQueue {
    LinkedList<Integer> A = new LinkedList<Integer>(); ;
    LinkedList<Integer> B = new LinkedList<Integer>();;
    public CQueue() {
         A = new LinkedList<Integer>();
         B = new LinkedList<Integer>();
    }
    

    public void appendTail(int value) {
     A.addLast(value);
    }
    
    public int deleteHead() {
    if(B.isEmpty() == false) return B.removeLast();
    if(A.isEmpty() == true) return -1;
    while(A.isEmpty() == false)
    B.addLast(A.removeLast());
    return B.removeLast(); 

 }
}

/**

 * Your CQueue object will be instantiated and called as such:
 * CQueue obj = new CQueue();
 * obj.appendTail(value);
 * int param_2 = obj.deleteHead();
   */
```


