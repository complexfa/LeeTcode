### [剑指 Offer 20. 表示数值的字符串](https://leetcode.cn/problems/biao-shi-shu-zhi-de-zi-fu-chuan-lcof/)

### 题目：

请实现一个函数用来判断字符串是否表示数值（包括整数和小数）。

```
数值（按顺序）可以分成以下几个部分：
1.若干空格
2.一个 小数 或者 整数
3.（可选）一个 'e' 或 'E' ，后面跟着一个 整数
4.若干空格
小数（按顺序）可以分成以下几个部分：
1.（可选）一个符号字符（'+' 或 '-'）
2.下述格式之一：
	至少一位数字，后面跟着一个点 '.'
	至少一位数字，后面跟着一个点 '.' ，后面再跟着至少一位数字
	一个点 '.' ，后面跟着至少一位数字
整数（按顺序）可以分成以下几个部分：
1.（可选）一个符号字符（'+' 或 '-'）
2.至少一位数字部分数值列举如下：["+100", "5e2", "-123", "3.1416", "-1E-16", "0123"]
部分非数值列举如下：["12e", "1a3.14", "1.2.3", "+-5", "12e+5.4"]
```

### 思路：有限无穷自动机

根据题意归纳出十种状态，非终结符为空格，数字，小数点，幂符号和正负号，画出状态转化图，初态为状态0，终态为状态2，3，7，8

![image-20230628201728979](E:\Leetcode\剑指offer\image-20230628201728979.png)

1.根据状态转化图写出以键值对的形式构造Map

2.从初态开始，遍历字符串中每一个元素值，并查找表中是否有属于该终结符的转换状态，如果没有返回false，如果有，p更新，继续循环

3.如果最终p值属于终态集说明属于表示数值的字符串。

```
class Solution {
    public boolean isNumber(String s) {
            Map[] states = {
                new HashMap<>(){{put(' ',0);put('s',1);put('d',2);put('.',4);}},
                new HashMap<>(){{put('d',2);put('.',4);}},
                new HashMap<>(){{put(' ',8);put('e',5);put('d',2);put('.',3);}},
                new HashMap<>(){{put('e',5);put('d',3);put(' ',8);}},
                new HashMap<>(){{put('d',3);}},
                new HashMap<>(){{put('d',7);put('s',6);}},
                new HashMap<>(){{put('d',7);}},
                new HashMap<>(){{put(' ',8);put('d',7);}},
                new HashMap<>(){{put(' ',8);}},
                };
            int p = 0;
            char t;
            for(char c: s.toCharArray()){
                if(c == ' ') t = ' ';
                else if (c == '+' || c == '-') t = 's';
                else if (c == 'e' || c == 'E') t = 'e';
                else if (c >= '0' && c <= '9') t ='d';
                else if (c == '.') t = '.';
                else t = '?';
                if(!states[p].containsKey(t)) return false;
                p = (int)states[p].get(t);
            }
            return p == 2 ||p == 3||p == 7||p == 8;
    }
}
```



