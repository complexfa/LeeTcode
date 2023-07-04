## [剑指 Offer 56 - I. 数组中数字出现的次数](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

### 题目：

一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)。

```
示例 1：
输入：nums = [4,1,4,6]
输出：[1,6] 或 [6,1]
示例 2：
输入：nums = [1,2,10,4,1,4,3,3]
输出：[2,10] 或 [10,2]
```

### 思路：异或运算

通过异或运算可知，相同的数字异或为0

存在有两个数字出现了两次，则n = x1 ^ x2 ^ x1 ^ x4 = 0 ^ x2 ^ x4 = x2 ^ x4

由异或性质可知，两个不同的数字异或至少有1位是1，求出最低的1位，分为两组

通过与运算，求出最低的1位，即m的值

再遍历数组，求m和数组中数的与，如果为0，那么为0的组再次异或，得出的值为其中一个结果，如果为1，那么为1的组进行异或，得出的值为第二个结果。

```
class Solution {
    public int[] singleNumbers(int[] nums) {
       int m = 1,n = 0,x = 0,y = 0;
       for(int num : nums){
            n ^= num;
       }
       while( (m & n) == 0){
           m <<= 1;
       }
       for(int num : nums){
           if((m & num) == 0) x ^= num;
           else y ^= num;
       }
       return new int[]{x,y};

    }
}
```

