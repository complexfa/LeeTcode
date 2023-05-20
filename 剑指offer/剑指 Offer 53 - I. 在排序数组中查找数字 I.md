### [剑指 Offer 53 - I. 在排序数组中查找数字 I](https://leetcode.cn/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

#### 题目：

统计一个数字在排序数组中出现的次数。

```
示例 1:
输入: nums = [5,7,7,8,8,10], target = 8
输出: 2

示例 2:
输入: nums = [5,7,7,8,8,10], target = 6
输出: 0
```

#### 思路：二分查找

通过两次的二分查找，第一次二分查找找到右边界，当指向数值小于等于target时，指针右移。第二次通过寻找比target小的数字找出其左边界，因为为排序数组，所以可以通过他们两个相减求得数字在排序数组中出现的次数。

```
class Solution {
    public int search(int[] nums, int target) {
       return midSearch(nums,target) - midSearch(nums,target - 1);
    }
    public int midSearch(int[] nums,int target){
       int l = 0,r = nums.length - 1,mid;
       while(l <= r){
           mid = (l + r) / 2;
           if(nums[mid] <= target) l = mid + 1; 
           if(nums[mid] > target) r = mid - 1;
       }
       return r;
    }
}
```

