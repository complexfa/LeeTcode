### [剑指 Offer 13. 机器人的运动范围](https://leetcode.cn/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/)

#### 题目：

地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子

#### 思路：

通过回溯，dfs

假设 m = 2,n = 3,k = 1

进行数位和计算，数位和计算函数

int NumSum（int i）

| <u>[0,0]</u> | <u>[0,1]</u> | [0,2] |
| ------------ | ------------ | ----- |
| <u>[1,0]</u> | [1,1]        | [1,2] |

由数位和可分析出，满足数位和的方格组成了一个等腰三角形，这些方格组成可达解。

设置一个辅助矩阵记录是否已经访问过，当数组越界，两个数的数位和大于k或已经访问过时返回false,其余情况进行下和右的访问，返回该坐标下可到达的各自数即1+右边格子可到达的格子数+下边各自可到达的格子数

例：k= 2

| <u>[0,0]</u>6 | <u>[0,1]</u>下方元素重复访问，2 | <u>[0,2]</u>1 | [0,3] |
| ------------- | ------------------------------- | ------------- | ----- |
| <u>[1,0]</u>3 | <u>[1,1]</u>1                   | [1,2]         | [1,3] |
| <u>[2,0]</u>1 | [2,1]                           | [2,2]         | [2,3] |
| [3,0]         | [3,1]                           | [3,2]         | [3,3] |
| [4,0]         | [4,1]                           | [4,2]         | [4,3] |

```
class Solution { 
    boolean visited[][];
    int m,n,k;
    public int NumSum(int i){
        int sum = 0;
        while(i != 0){
            sum += (i % 10);
            i = i / 10;
        }
        System.out.println(sum);
        return sum;
    }
    
    public int movingCount(int m, int n, int k) {
        this.m = m; 
        this.n = n;
        this.k = k;
        visited = new boolean[m][n];
        return dfs(0,0,k);
    }
    
    public int dfs(int i,int j,int k){
        if(i >= m || j >= n||NumSum(i) + NumSum(j)> k||visited[i][j]){
            return 0;
        }
        visited[i][j] = true;
        return 1 + dfs(i+1,j,k) + dfs(i,j+1,k);
    }
}
```

