### [剑指 Offer 21. 调整数组顺序使奇数位于偶数前面](https://leetcode.cn/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

#### 题目：

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数在数组的前半部分，所有偶数在数组的后半部分。

####  思路：

双指针

循环中再次判断的原因是，移动指针的过程中还是会出现i>j的情况所以需要再次判断。

```
class Solution {
    public boolean isEven(int i){
        if(i % 2 == 0)
           return true;
        else
           return false; 
    }
    public int[] exchange(int[] nums) {
        int i = 0;
        int j = nums.length - 1;
        while(i < j){
          while(i < j &&!isEven(nums[i])) i++;
          while(i < j &&isEven(nums[j])) j--;
          int temp = nums[i];
          nums[i] = nums[j];
          nums[j] = temp; 
        }
        return nums;
    }
}

```

