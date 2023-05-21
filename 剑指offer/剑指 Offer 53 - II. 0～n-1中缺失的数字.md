### [剑指 Offer 53 - II. 0～n-1中缺失的数字](https://leetcode.cn/problems/que-shi-de-shu-zi-lcof/)

#### 题目：

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

```
示例 1:
输入: [0,1,3]
输出: 2

示例 2:
输入: [0,1,2,3,4,5,6,7,9]
输出: 8
```

#### 思路：

通过数组循环，时间复杂度O(n)

```
class Solution {
    public int missingNumber(int[] nums) {
        for(int i = 0;i < nums.length;i++){
            if(nums[i] != i) return i;
        }
        return nums.length ;
    }
}
```

通过二分查找，时间复杂度O(logN)

通过二分折半，如果nums[mid] == mid时，那么目标元素在右半部分，如果不等于，那么目标元素在左半部分

```
class Solution {
    public int missingNumber(int[] nums) {
        int l = 0,r = nums.length - 1,mid;
        while(l <= r){
           mid = (l + r) / 2;
           if(nums[mid] == mid) l = mid + 1;
           else r = mid - 1;
        }
       return l;
    }
}
```

