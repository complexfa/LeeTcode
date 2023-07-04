## [剑指 Offer 60. n个骰子的点数](https://leetcode.cn/problems/nge-tou-zi-de-dian-shu-lcof/)

### 题目：

把n个骰子扔在地上，所有骰子朝上一面的点数之和为s。输入n，打印出s的所有可能的值出现的概率。

你需要用一个浮点数数组返回答案，其中第 i 个元素代表这 n 个骰子所能掷出的点数集合中第 i 小的那个的概率。

```
示例 1:
输入: 1
输出: [0.16667,0.16667,0.16667,0.16667,0.16667,0.16667]
```

### 思路：动态规划

每个骰子的数字有1-6，n个骰子的范围为[n,6n]，即n个骰子有6n-n+1=5n+1个点数集合。

如果n个骰子的解为f(n),点数和为f(n,x)，那么加入一个新的骰子，假设值为1，那么则是f(n,x-1)，如果值为2，那么则是f(n,x-2)

![image-20230704203727961](E:\Leetcode\剑指offer\image-20230704203727961.png)

```
class Solution {
    public double[] dicesProbability(int n) {
        double[] dp = new double[6];
        //初始化dp为骰子数为1个时点数和的概率
        Arrays.fill(dp,1.0 / 6.0);
        //循环相加n个骰子
        for(int i = 2;i <= n;i++){
        //创建temp记录下一个骰子的点数和
            double[] temp = new double[5 * i + 1];
            //遍历n-1个骰子的解（点数和）
            for(int k = 0;k < dp.length;k++){
            //将他们的六个情况的贡献相加得到骰子k+j点数和的概率
                for(int j = 0;j < 6;j++){
                    temp[k + j] += dp[k] / 6.0; 
                }
            }
            //两个数组交替进行
            dp = temp;
        }   
        return dp;
    }
}
```

