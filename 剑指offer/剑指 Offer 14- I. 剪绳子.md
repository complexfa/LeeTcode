#### [剑指 Offer 14- I. 剪绳子](https://leetcode.cn/problems/jian-sheng-zi-lcof/)

#### 给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m-1] 。请问 k[0]*k[1]*...*k[m-1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。
一般这种拆分求最大的问题就容易想到动态规划和贪心。我就研究了一下动态规划。

如果一直不停的做拆分求最优就可以得到最终的最优

最优子结构是dp[i]=maxn(maxn,max(j *(i-j),j*dp[i-j])

为什么i从2开始，是因为0和1不能拆分，拆除来乘只能是0

要注意数组定义时要n+1个空间

因为要一直算到dp[n]而不是dp[n-1]就结束了

```
class Solution {
    public int cuttingRope(int n) {
        int[] dp = new int[n + 1];
        for (int i = 2 ;i <= n; i++){
              int max = 0;
            for(int j = 1 ;j < i;j++){
                max = Math.max(max,Math.max(j * (i - j),j * dp[i - j]));
            }   
          dp[i] = max;
        }
        return dp[n];
    }
}
```

