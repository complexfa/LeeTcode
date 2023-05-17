### [剑指 Offer 29. 顺时针打印矩阵](https://leetcode.cn/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)

#### 题目：

输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字。

| 1    | 2    | 3    |
| ---- | ---- | ---- |
| 4    | 5    | 6    |
| 7    | 8    | 9    |

| 1    | 2    | 3    | 4    |
| ---- | ---- | ---- | ---- |
| 5    | 6    | 7    | 8    |
| 9    | 10   | 11   | 12   |

#### 思路：

根据从左到右，从上到下，从右到左，从下到上的顺序进行打印

设置t,b,l,r四个值代表打印的行列，t = 0，b = matrix.length() - 1

l = 0,r = matrix[0].length() - 1

从左到右打印，即从 l 到 r  ，t++， 当 t > b 时停止;

从上到下打印，即从 t 到 b ，r--,  当 l > r 时停止;

从右到左打印，即从 r 到 l  ，b--, 当 t > b  时停止;

从下到上打印，即从 b 到 t ，l++, 当 l > r  时停止;

**注意：当数组只有一行时的特殊情况。**

```
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        if(matrix.length == 0) return new int[0];
        int t = 0,b = matrix.length - 1;
        int l = 0,r = matrix[0].length - 1;
        int[] a = new int[(b + 1) * (r + 1)];
        int cur = 0;
        while(true){
            for(int i = l;i <= r;i++){
                a[cur++] = matrix[t][i];
            }
            if(++t > b) break;
            for(int i = t;i <= b;i++){
                a[cur++] = matrix[i][r];
            }
            if(--r < l) break;
            for(int i = r;i >= l;i--){
                a[cur++] = matrix[b][i];
            }
            if(--b < t) break;
            for(int i = b;i >= t;i--){
                a[cur++] = matrix[i][l];
            }
            if(++l > r) break;
        }
        return a;
    }
}
```

