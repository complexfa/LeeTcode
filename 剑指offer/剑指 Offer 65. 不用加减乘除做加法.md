### [剑指 Offer 65. 不用加减乘除做加法](https://leetcode.cn/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/)

#### 题目：

写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号。

```
示例:
输入: a = 1, b = 1
输出: 2
```

#### 思路：位运算，递归

s = a + b = 非进位+进位

通过非进位和进位相加，非进位是通过异或运算，进位是与运算并且向左移一位，不断进行递归，直到进位为0为止。

```
class Solution {
    public int add(int a, int b) {
       if(b == 0)
         return a;

       return add(a ^ b,(a & b) << 1);
    }

    
}
```

