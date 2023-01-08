#### [剑指 Offer II 003. 前 n 个数字二进制中 1 的个数](https://leetcode.cn/problems/w3tCBm/)

给定一个非负整数 `n` ，请计算 `0` 到 `n` 之间的每个数字的二进制表示中 1 的个数，并输出一个数组。

#### 思路：

动态规划

每个数中1的个数为该数除以2的商数中1的个数加上余数

其状态方程为：

dp[i] = dp[i/2] + i%2;

```
class Solution {
    public int[] countBits(int n) {
       int[] dp = new int[n + 1];
       dp[0] = 0;
       if(n == 0)
       return dp;
       dp[1] = 1;
       for(int i = 2; i <= n;i++){
           dp[i] = dp[i/2] + i % 2;
       }
       return dp;
    }
}
```

