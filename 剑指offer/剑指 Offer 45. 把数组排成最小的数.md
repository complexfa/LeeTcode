## [剑指 Offer 45. 把数组排成最小的数](https://leetcode.cn/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

### 题目：

输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。

```
示例 1:
输入: [10,2]
输出: "102"
示例 2:
输入: [3,30,34,5,9]
输出: "3033459"
```

#### 思路：利用快速排序

本质上进行字符串的排序，即：

x + y > y + x，此时x > y，x在y的右边

x + y < y + x，此时x < y，x在y的左边。

传递性可证明

```
class Solution {
    public String minNumber(int[] nums) {
            String[] str = new String[nums.length];
            for(int i = 0;i < nums.length;i++){
                str[i] = String.valueOf(nums[i]);
            }
            quickSort(str,0,nums.length - 1);
            StringBuilder sb = new StringBuilder();
            for(String st : str){
                sb.append(st);
            }
            return sb.toString();
    }
    public void quickSort(String[] str,int l,int r){
            if(l >= r) return;
            int i = l,j = r;
            String temp = str[i];
            while(i < j){
                while((str[l] + str[j]).compareTo(str[j] + str[l]) <= 0 && i < j) j--;
                while((str[i] + str[l]).compareTo(str[l] + str[i]) <= 0 && i < j) i++;
                temp = str[i];
                str[i] = str[j];
                str[j] = temp;
            }
            str[i] = str[l];
            str[l] = temp;
            quickSort(str,l,i - 1);
            quickSort(str,i + 1,r); 
    }
}
```

