#### [剑指 Offer 03. 数组中重复的数字](https://leetcode.cn/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

找出数组中重复的数字。在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

1.暴力解法

这个方法最容易想到，但是时间复杂度和空间复杂度都很高

```
class Solution {
    public int findRepeatNumber(int[] nums) {
        for(int i = 0; i < nums.length;i++){
            for(int j = i + 1;j < nums.length;j++){
                if(nums[i] == nums[j]){
                    return nums[i];
                }
            }
        }
        return -1;
    }
}
```

2.哈希表解法

这个一开始也想到过，但是不太熟练Java中的哈希表怎么用的

```
class Solution {
    public int findRepeatNumber(int[] nums) {
     Set<Integer> s = new HashSet<>();
     for(int num : nums){
         if(s.contains(num)) return num;
         s.add(num);
     }
     return -1;
    }
}
```

时间复杂度 O(N)： 遍历数组使用 O(N) ，HashSet 添加与查找元素皆为 O(1) 。
空间复杂度 O(N)： HashSet 占用 O(N) 大小的额外空间。
