### [剑指 Offer 61. 扑克牌中的顺子](https://leetcode.cn/problems/bu-ke-pai-zhong-de-shun-zi-lcof/)

#### 题目：

从若干副扑克牌中随机抽 5 张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14。

```
示例 1:
输入: [1,2,3,4,5]
输出: True
示例 2:
输入: [0,0,1,2,5]
输出: True
```

#### 思路：Set集合判重

作为顺子，其最大牌-最小牌值应当小于5

如果遇到大小王则跳过，遇到其他更新最大最小值，通过res集合判断是否有重复牌，如果有，则直接返回false，如果没有加入。最终根据最大牌减最小牌的数值与5比较返回布尔值

```
class Solution {
    public boolean isStraight(int[] nums) {
        Set<Integer> res = new HashSet<>();
        int max = 0,min = 14;
        for(int i = 0;i < nums.length;i++){
            if(nums[i] == 0) continue;
            max = Math.max(max,nums[i]);
            min = Math.min(min,nums[i]);
            if(res.contains(nums[i])) return false;
            res.add(nums[i]);
        }
        if(max - min < 5) return true;
        else return false;
    }
}
```

