#### [剑指 Offer 04. 二维数组中的查找](https://leetcode.cn/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)

#### 题目：

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

 二维数组列数：matrix[0].length

行数：matrix.length

```
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
             int i = matrix.length - 1;
             int j = 0;
             while(i >= 0 && j < matrix[0].length)
             {
             if(matrix[i][j] > target) i--;
             else if(matrix[i][j] < target) j++;
             else  return true; 
            }
               return false;
         }
    
}
```


将二维数组最左下角的数与target先进行比较

1.如果比target大，那么target在该数的上侧，删除该行

2.如果比target小，那么target在该数的右侧，删除该列

时间复杂度 O(M+N)
空间复杂度 O(1)
