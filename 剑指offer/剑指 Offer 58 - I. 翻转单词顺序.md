### [剑指 Offer 58 - I. 翻转单词顺序](https://leetcode.cn/problems/fan-zhuan-dan-ci-shun-xu-lcof/)

#### 题目：

输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"。

```
示例 1：
输入: "the sky is blue"
输出: "blue is sky the"
示例 2：
输入: "  hello world!  "
输出: "world! hello"
解释: 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。
示例 3：
输入: "a good   example"
输出: "example good a"
解释: 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。
```

#### 思路：双指针

通过从后向前遍历字符串，先消除两边空格，如果前指针遇到空格，则把前指针到后指针中间这段字符串加入StringBuilder,再清除中间的空格直到遇见新的字母，将后指针移到此处，前指针继续循环。

```
class Solution {
    public String reverseWords(String s) {
        s.trim();
        int i = s.length() - 1,j = i;
        StringBuilder sb = new StringBuilder();
        while(i >= 0){
            while(i >= 0 && s.charAt(i) != ' ') i--;
            sb.append(s.substring(i + 1,j + 1) + " ");
            while(i >= 0 && s.charAt(i) == ' ') i--;
            j = i;
        } 
        return sb.toString().trim();
    }
}
```

