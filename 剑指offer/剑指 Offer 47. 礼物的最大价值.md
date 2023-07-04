## [剑指 Offer 47. 礼物的最大价值](https://leetcode.cn/problems/li-wu-de-zui-da-jie-zhi-lcof/)

### 题目：

在一个 m*n 的棋盘的每一格都放有一个礼物，每个礼物都有一定的价值（价值大于 0）。你可以从棋盘的左上角开始拿格子里的礼物，并每次向右或者向下移动一格、直到到达棋盘的右下角。给定一个棋盘及其上面的礼物的价值，请计算你最多能拿到多少价值的礼物？

```
示例 1:
输入: 
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
输出: 12
解释: 路径 1→3→5→2→1 可以拿到最多价值的礼物
```

### 思路：动态规划

因为只能向下或者向右移动，所以可以得到动态转移方程，再考虑边界情况，只能下移或者右移

i=0 ,j=0，为其本身值

i=0,j!=0，为其左边格子价值加自身价值

i!=0,j=0，为其上边格子价值加自身价值

i!=0,j!=0，为其左边格子和上边格子的最大值加自身价值

```
class Solution {
    public int maxValue(int[][] grid) {
        for(int i = 0;i < grid.length;i++)
            {
                for(int j = 0;j < grid[i].length;j++){
                    if(i == 0 && j != 0) grid[i][j] = grid[i][j - 1] + grid[i][j];
                    if(i != 0 && j == 0) grid[i][j] = grid[i - 1][j] + grid[i][j];
                    if(i != 0 && j != 0) grid[i][j] = Math.max(grid[i - 1][j], grid[i][j - 1])+ grid[i][j];
                }
            }
        return grid[grid.length - 1][grid[0].length - 1];
    }
}
```

