## [剑指 Offer 46. 把数字翻译成字符串](https://leetcode.cn/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)

### 题目：

给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法。

```
示例 1:
输入: 12258
输出: 5
解释: 12258有5种不同的翻译，分别是"bccfi", "bwfi", "bczi", "mcfi"和"mzi"
```

### 思路：动态规划

只有1-25可单独翻译，可以得出规律

当xn-1xn可以单独翻译时，f(n) = f(n-1) + f(n-2)

当xn-1xn不可以被单独翻译时，f(n) = f(n-1)

| 1       | 2       | 2        | 5    | 8    |      |
| ------- | ------- | -------- | ---- | ---- | ---- |
|         |         |          | x    | y    |      |
|         |         |          | c= 1 | a=1  | b=1  |
| 1       | 2       | 2        | 5    | 8    |      |
|         |         | x        | y    |      |      |
|         |         | c= a+b=2 | a=1  | b=1  |      |
| 1       | 2       | 2        | 5    | 8    |      |
|         | x       | y        |      |      |      |
|         | c=a+b=3 | a=2      | b=1  |      |      |
| 1       | 2       | 2        | 5    | 8    |      |
| x       | y       |          |      |      |      |
| c=a+b=5 | a=3     | b=2      |      |      |      |

```
class Solution {
    public int translateNum(int num) { 
        int a = 1,b = 1;
        int x, y = num % 10;
        while(num != 0){
            num /= 10;
            x = num % 10;
            int temp = 10 * x + y;
            int c = (temp >=10 && temp <=25) ? a + b : a;
            b = a;
            a = c;
            y = x;
        }
        return a;
    }
}
```

