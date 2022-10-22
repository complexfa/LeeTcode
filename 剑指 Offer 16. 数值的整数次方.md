#### [剑指 Offer 16. 数值的整数次方](https://leetcode.cn/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

#### 实现 [pow(*x*, *n*)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 x 的 n 次幂函数（即，xn）。不得使用库函数，同时不需要考虑大数问题。

 先考虑特殊情况x=0和n=0时，为了减少时间复杂度，我们二分进行运算，如果与2求余等于0，那么相乘即是答案，如果求余余1，就要判断n是否大于0，如果是大于，那么再乘以他本身，如果小于，那么除以他本身

```
class Solution {
    public double myPow(double x, int n) {
       if (x == 0)
       return 0;
       if(n == 0)
       return 1;
       double m = myPow(x , n/2);
       if(n%2 ==0)
       return m * m;
       return n > 0 ? m * m * x : m * m / x;
    }
}
```


