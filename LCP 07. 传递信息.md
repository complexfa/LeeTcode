#### [LCP 07. 传递信息](https://leetcode.cn/problems/chuan-di-xin-xi/)

小朋友 A 在和 ta 的小伙伴们玩传信息游戏，游戏规则如下：

有 n 名玩家，所有玩家编号分别为 0 ～ n-1，其中小朋友 A 的编号为 0
每个玩家都有固定的若干个可传信息的其他玩家（也可能没有）。传信息的关系是单向的（比如 A 可以向 B 传信息，但 B 不能向 A 传信息）。
每轮信息必须需要传递给另一个人，且信息可重复经过同一个人
给定总玩家数 n，以及按 [玩家编号,对应可传递玩家编号] 关系组成的二维数组 relation。返回信息从小 A (编号 0 ) 经过 k 轮传递到编号为 n-1 的小伙伴处的方案数；若不能到达，返回 0。

#### 思路：

##### 深度优先搜索

|      | 0    | 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 0    |      |      | 1    |      | 1    |
| 1    |      |      |      |      | 1    |
| 2    | 1    | 1    |      | 1    |      |
| 3    |      |      |      |      | 1    |
| 4    |      |      |      |      |      |

也可以画出有向图进行理解

对于0节点所有路径情况进行遍历，如果步数为k并且终点为n-1,那么计数器加一

```
class Solution {
    int count = 0;
    public int numWays(int n, int[][] relation, int k) {
        int[][] map = new int[n][n];
        for(int i = 0; i < relation.length;i++){
            map[relation[i][0]][relation[i][1]] = 1;
        }
        dfs(0,0,n,0,map,k);
        return count;
    }
    public void dfs(int i,int j,int n,int step,int[][] map,int k){
       if(i >=n ||j >=n)
       return;
       if(step == k && i == n - 1){
           count++;
           return;
       }else if(step >= k){
           return;
       }
       for(int m = j; m < n;m++){
           if(map[i][m] == 1){
               dfs(m,0,n,step + 1,map,k);
           }
       }
       return;
    }
}
```

