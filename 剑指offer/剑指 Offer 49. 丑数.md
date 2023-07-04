## [剑指 Offer 49. 丑数](https://leetcode.cn/problems/chou-shu-lcof/)

### 题目：

我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数。

示例:

```
输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。
```

说明: 

1.1 是丑数。
2.n 不超过1690。

### 思路：动态规划

丑数只能由某个丑数×2，×3，×5获得

从小到大排序求出前n个丑数

| 1     |      |      |      |      |      |
| ----- | ---- | ---- | ---- | ---- | ---- |
| a,b,c |      |      |      |      |      |
| 1     | 2    |      |      |      |      |
| b,c   | a    |      |      |      |      |
| 1     | 2    | 3    |      |      |      |
| c     | a,b  |      |      |      |      |
| 1     | 2    | 3    | 4    |      |      |
| c     | b    | a    |      |      |      |
| 1     | 2    | 3    | 4    | 5    |      |
|       | b,c  | a    |      |      |      |

```
class Solution {
    public int nthUglyNumber(int n) {
        int[] dp = new int[n];
        dp[0] = 1;
        int a = 0,b = 0,c = 0;
        for(int i = 1; i < n;i++){
            dp[i] = Math.min(Math.min(dp[a] * 2, dp[b] * 3),dp[c] * 5);
            if(dp[i] == (dp[a] * 2)) a++;
            if(dp[i] == (dp[b] * 3)) b++;
            if(dp[i] == (dp[c] * 5)) c++;
        }
        return dp[n - 1];
    }
}
```

