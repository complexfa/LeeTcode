#### [剑指 Offer 42. 连续子数组的最大和](https://leetcode.cn/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。

要求时间复杂度为O(n)。

#### 思路：

动态规划

dp[i]表示到num[i]的连续子数组和

如果dp[i-1]<0,那么其对后面的数而言是拉低了它的最大值，所以分两种情况讨论

如果dp[i-1] >0,dp[i] = dp[i -1]+nums[i]

如果dp[i -1] <=0,dp[i] = nums[i];

再通过比较dp[i]的大小，可以求得子数组的最大和

| nums[i] | -2   | 1    | -3   | 4    | -1   | 2    | 1    | -5   | 4    |
| ------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| dp[i]   | -2   | 1    | -2   | 4    | 3    | 5    | 6    | 1    | 5    |

```
class Solution {
    public int maxSubArray(int[] nums) {
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        int max = dp[0];
        for(int i = 1;i < nums.length;i++){
            if(dp[i - 1] > 0)
            dp[i] = dp[i - 1] + nums[i];
            if(dp[i - 1] <= 0)
            dp[i] = nums[i];
            max = Math.max(dp[i],max);
        }
        return max;
    }
}
```

