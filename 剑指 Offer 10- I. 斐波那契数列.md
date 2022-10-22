## [剑指 Offer 10- I. 斐波那契数列](https://leetcode.cn/problems/fei-bo-na-qi-shu-lie-lcof/)

#### 写一个函数，输入 `n` ，求斐波那契（Fibonacci）数列的第 `n` 项（即 `F(N)`）。斐波那契数列的定义如下：

```
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
```

#### 斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

#### 答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

这题困扰我的就是取模问题，我发现得每次算出的都取模才可以。

但是这种方法复杂度好像挺高的，官方给的矩阵快速幂方法还没咋明白，等我搞明白了再补充吧

```
class Solution {
    public int fib(int n) {
    if(n == 0) return 0;
    if(n == 1) return 1;
    if(n == 2) return 1;
    int [] a = new int[n + 1];
    a[0] = 0;
    a[1] = 1;
    a[2] = 1;
    for(int i = 3;i <= n;i++){
      a[i] = (a[i - 1] + a[i - 2]) % 1000000007;
    }
    return a[n];
    }
}
```


