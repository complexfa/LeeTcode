### [剑指 Offer 50. 第一个只出现一次的字符](https://leetcode.cn/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

#### 题目：

在字符串 s 中找出第一个只出现一次的字符。如果没有，返回一个单空格。 s 只包含小写字母。

```
示例 1:
输入：s = "abaccdeff"
输出：'b'

示例 2:
输入：s = "" 
输出：' '
```

#### 思路：哈希表

通过键值对统计每个元素出现的次数，再顺序遍历字符串，返回第一个值为1的元素。

```
class Solution {
    public char firstUniqChar(String s) {
       Map<Character,Integer> map = new HashMap<>();
       for(int i = 0;i < s.length();i++){
           char c = s.charAt(i);
           if(map.containsKey(c)){
               map.put(c,map.get(c) + 1);
           }else{
               map.put(c,1);
           }
       }
       for(int i = 0;i < s.length();i++){
           if(map.get(s.charAt(i)) == 1) return s.charAt(i);
       }
       return ' ';
    }
}
```

通过布尔值来进行判断，如果出现一次，那么布尔值为true,如果出现多次，布尔值变为false，最终顺序遍历字符串元素，返回第一个为true的元素，该方法可以节省空间。

```
class Solution {
    public char firstUniqChar(String s) {
       Map<Character,Boolean> map = new HashMap<>();
       char[] ch = s.toCharArray();
       for(char c:ch)
          map.put(c,!map.containsKey(c));
       for(char c:ch)
          if(map.get(c)) return c;
      return ' ';
    }
}
```

