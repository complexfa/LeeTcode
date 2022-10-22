#### [剑指 Offer 12. 矩阵中的路径](https://leetcode.cn/problems/ju-zhen-zhong-de-lu-jing-lcof/)
给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。
单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。
该题用的是深度优先搜索和回溯剪枝。

方法挺容易想到的，但是代码还是不咋会写

看完大佬代码差不多明白流程了，自己敲了一遍也成功了嘿！

思路大概就是：在数组越界或者元素不匹配时返回false

如果已经搜索完word中最后一个元素时返回true

我们要记住一定要改变board[i][j]的值，如果不改变的话搜索后面一个元素的时候，经过四面的搜索很可能又会是他！那样就重复搜索了。

然后用res记录目标数组中接下来一个元素能否搜索到。

还要记得还原board[i][j]的值，因为如果这条路找不到的话，通过其他路说不定兜兜转转还是会用到他的

```
class Solution {
    public boolean exist(char[][] board, String word) {
       char[] w = word.toCharArray();
       for(int i = 0;i < board.length; i++){
           for(int j = 0;j < board[0].length; j++){
               if(dfs(board,w,i,j,0)) return true;
           }
       }
       return false;
    }

    boolean dfs(char[][] board,char[] w,int i, int j, int k){
        if(i < 0||i >= board.length||j < 0||j >= board[0].length||board[i][j] != w[k]) return false;
        if(k == w.length - 1) return true;
     
        board[i][j] = 0;
        boolean res = dfs(board,w,i + 1,j,k + 1)||dfs(board,w,i - 1,j,k + 1)||dfs(board,w,i,j - 1,k + 1)||dfs(board,w,i,j + 1,k + 1);
        board[i][j] = w[k];
        return res;
    }

}
```


