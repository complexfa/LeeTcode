### [剑指 Offer 38. 字符串的排列](https://leetcode.cn/problems/zi-fu-chuan-de-pai-lie-lcof/)

#### 题目：

输入一个字符串，打印出该字符串中字符的所有排列。

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

```
示例:
输入：s = "abc"
输出：["abc","acb","bac","bca","cab","cba"]
```

#### 思路：回溯法

每次固定一个字母

```
class Solution {
    List<String> res = new LinkedList<>();
    char[] c;
    public String[] permutation(String s) {
        c = s.toCharArray();//转化为字符数组
        dfs(0);
        return res.toArray(new String[res.size()]);//转换为字符串数组
    }
    public void dfs(int x){
       if(x == c.length - 1) {
            res.add(String.valueOf(c));
            return;
            //说明已经遍历到结尾，转为字符串加入结果集
        }
        HashSet<Character> set = new HashSet<>();
        //通过哈希Set去除重复元素的判断
        for(int i = x ;i < c.length;i++){
            if(set.contains(c[i])) continue;
            set.add(c[i]);
            //如果是重复元素则跳过
            swap(i,x);
            //固定一个元素
            dfs(x + 1);
            swap(i,x);
            //回溯
        }
    }
    public void swap(int a,int b){
        char temp = c[a];
        c[a] = c[b];
        c[b] = temp;
    }
}
```

