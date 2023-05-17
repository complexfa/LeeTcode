## [剑指 Offer 05. 替换空格](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/)

#### 请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。

ToCharArray( )的用法，将字符串对象中的字符转换为一个字符数组

String 为不可变字符串

转换为StringBuilder为可变字符串类

public StringBuilder()	创建一个空白的可变的字符串对象，不包含任何内容
public String toString()	通过toString就可以实现把StringBuilder转换为String



```
class Solution {
    public String replaceSpace(String s) {
          StringBuilder sbr= new StringBuilder();
          for(char c : s.toCharArray()){
              if(c == ' ') sbr.append("%20");
              else sbr.append(c);
          }
          return sbr.toString();
    }
}
```