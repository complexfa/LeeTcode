## [剑指 Offer 63. 股票的最大利润](https://leetcode.cn/problems/gu-piao-de-zui-da-li-run-lcof/)

### 题目：

假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？

```
示例 1:
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
 注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。
示例 2:
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
```

### 思路：动态规划

遍历比较得出最低股票价格同时比较当前利润与第i日减去已知最小值中的最大值，求出最大利润。

当前最大利润=max（当前最大利润 ，第i日价格 - 已知最低价）

```
class Solution {
    public int maxProfit(int[] prices) {
       int profit = 0,cost = Integer.MAX_VALUE;
       for(int i = 0;i < prices.length;i++){
          cost = Math.min(cost,prices[i]);
          profit = Math.max(profit, prices[i] - cost);
       }
       return profit;
    }
}
```

