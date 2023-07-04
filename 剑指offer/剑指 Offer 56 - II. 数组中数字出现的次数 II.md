## [剑指 Offer 56 - II. 数组中数字出现的次数 II](https://leetcode.cn/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

### 题目：

在一个数组 nums 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字。

```
示例 1：
输入：nums = [3,4,3,3]
输出：4
示例 2：
输入：nums = [9,1,7,9,7,9,7]
输出：1
```

### 思路：哈希Map

通过哈希Map判断数组中的该数字是否出现过，如果出现过那么该键的值加一，如果没出现过，加入该键值对，最后遍历哈希Map得出值为1的键。

```
class Solution {
    public int singleNumber(int[] nums) {
        Map<Integer,Integer> map = new HashMap<>();
        for(int i : nums){
            if(map.containsKey(i)) 
               map.put(i,map.get(i) + 1);
            else map.put(i,1);
        }
        for(Map.Entry<Integer,Integer> entry:map.entrySet()){
            if(entry.getValue() == 1){
                return entry.getKey();
            } 
        }
        return -1;  
    }
}  
```

