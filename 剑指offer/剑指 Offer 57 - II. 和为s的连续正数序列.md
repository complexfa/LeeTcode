

### [剑指 Offer 57 - II. 和为s的连续正数序列](https://leetcode.cn/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

#### 题目：

输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。

序列内的数字由小到大排列，不同序列按照首个数字从小到大排列。

```
示例 1：
输入：target = 9
输出：[[2,3,4],[4,5]]
示例 2：
输入：target = 15
输出：[[1,2,3,4,5],[4,5,6],[7,8]]
```

#### 思路：滑动窗口

通过双指针，如果当前窗口内元素相加小于目标值，将右指针向右移并把新的元素加入，如果当前窗口内元素相加大于目标值，则将左指针向右移并减去先前指向的元素，如果等于目标值，加入结果集，左指针向右移并减去先前指向的元素

```
class Solution {
    public int[][] findContinuousSequence(int target) {
       List<int[]> res = new ArrayList<>();
       int i = 1,j = 2,sum = 3;
       while(i < j){
           if(sum == target){
               int[] a = new int[j- i + 1];
               int n = 0;
               for(int m = i;m <= j;m++){
                   a[n++] = m;
               }
               res.add(a);
           }
           if(sum < target)  sum += ++j;
           else  sum -= i++;
       }
       return res.toArray(new int[0][]);
    }
}
```

