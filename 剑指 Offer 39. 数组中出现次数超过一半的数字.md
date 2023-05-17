### [剑指 Offer 39. 数组中出现次数超过一半的数字](https://leetcode.cn/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

#### 题目：

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

示例 1:

输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
输出: 2

#### 思路：

哈希表统计法：空间时间复杂度均为O(n)

通过键值对统计每个数字的数量，再进行遍历。

```
class Solution {
    public int majorityElement(int[] nums) {
    Map<Integer,Integer> map= new HashMap<>();
    for(int i = 0;i < nums.length;i++){
        int j = nums[i];
        if(map.containsKey(j)){
            map.put(j,map.get(j) + 1);
        }else{
            map.put(j,1);
        }
    }
    Set<Integer> keys = map.keySet();
    for(Integer key : keys){
        int value = map.get(key);
        if(value > nums.length / 2)
           return key;
    }
    return -1;
  }
}
```

数组排序法：

作为众数数组中点的元素一定为众数。

```
class Solution {
    public int majorityElement(int[] nums) {
      Arrays.sort(nums);
     return nums[nums.length / 2];
  }
}
```

摩尔投票法：时间复杂度O(n) 空间复杂度O(1)

* 若记众数的票数为+1，非众数的票数为-1，则一定有所有数字的票数和>0

* 若数组的前a个数字的票数和=0，则数组剩余(n-a)个数字的票数和一定仍>0，即后（n-a)个数字的众数仍为x。

  即一旦前面a个数字的票数和为0，那么即可以不看前面的a个数字

```
class Solution {
    public int majorityElement(int[] nums) {
      int votes = 0;
      int x = nums[0];
      for(int num : nums){
          if(votes == 0)
            x = num;
          if(num == x) votes++;
          else votes--;
      }
      return x;
  }
}
```

