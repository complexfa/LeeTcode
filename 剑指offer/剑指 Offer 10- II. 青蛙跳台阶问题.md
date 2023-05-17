#### [剑指 Offer 10- II. 青蛙跳台阶问题](https://leetcode.cn/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/)

#### 一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 `n` 级的台阶总共有多少种跳法。

#### 答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

求有多少种可能性------>递推性质

通过青蛙最后一步只能跳一级或者两级

最后一步跳一级的话，那么为f(n-1)种跳法

最后一步跳两级的话，那么为f(n-2)种跳法

将最后的两种情况相加就可以得到最终的跳法数

即f(n) = f(n-1)+f(n-2)

当只有一级台阶时，f(1) = 1;

当有两级台阶时，f(2) = 2;

```
class Solution {
    public int numWays(int n) {
        int a = 1,b = 2,sum = 0;
        if( n == 1 || n == 0) return 1;
        if( n == 2) return 2;
        for(int i = 3;i <= n;i++){
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;
        }
        return b;
    }
}
```

