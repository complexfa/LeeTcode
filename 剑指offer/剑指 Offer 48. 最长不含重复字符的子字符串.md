## [剑指 Offer 48. 最长不含重复字符的子字符串](https://leetcode.cn/problems/zui-chang-bu-han-zhong-fu-zi-fu-de-zi-zi-fu-chuan-lcof/)

### 题目：

请从字符串中找出一个最长的不包含重复字符的子字符串，计算该最长子字符串的长度。

```
示例 1:
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
示例 2:
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
示例 3:
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
请注意，你的答案必须是子串的长度，"pwke" 是一个子序列，不是子串。
```

### 思路：动态规划+滑动窗口

|      | a    | b    | c    | a    | b    | c    | b    | b    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| i    |      |      |      |      |      |      |      |      |
|      |      |      |      | j    |      |      |      |      |
|      | i    |      |      |      |      |      |      |      |
|      |      | i    |      |      | j    |      |      |      |
|      |      |      | i    |      |      | j    |      |      |
|      |      |      |      |      | i    |      | j    |      |
|      |      |      |      |      |      |      | i    | j    |

通过哈希表判断是否存在重复元素

如果有，更新i，更新哈希表，更新res

```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character,Integer> dic = new HashMap<>();
        int i = -1;
        int res = 0;
        for(int j = 0;j < s.length();j++){
            if(dic.containsKey(s.charAt(j))) 
               i = Math.max(i,dic.get(s.charAt(j)));
            dic.put(s.charAt(j),j);
            res = Math.max(res,j - i);
        }
        return res;
    }
}
```

