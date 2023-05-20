### [剑指 Offer 40. 最小的k个数](https://leetcode.cn/problems/zui-xiao-de-kge-shu-lcof/)

#### 题目：

输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

```
示例 1：
输入：arr = [3,2,1], k = 2
输出：[1,2] 或者 [2,1]

示例 2：
输入：arr = [0,1,2,1], k = 1
输出：[0]
```

#### 思路：快速排序

将数组第一个数作为基准值，左右与基准值比较，如果左边的指针指向的数比基准值大，右边指针的数比基准值小，那么交换两边的数。最后交换左右指针相等时指向的数，做到基准值左边的数都比他小，右边的数都比他大。当基准值的位置正好为k时，其左边的数均比他小即最小的k个数。

```
 while(i < j && arr[j] >= arr[l]) j--;
 while(i < j && arr[i] <= arr[l]) i++;
```

这两个语句不能交换位置，通过画图可知原因。

```
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        if(arr.length <= k)
        return arr;
        return QuickSort(arr,k,0,arr.length - 1);
    }
    public int[] QuickSort(int[] arr,int k,int l,int r){
        int i = l,j = r;
        while (i < j){
            while(i < j && arr[j] >= arr[l]) j--;
            while(i < j && arr[i] <= arr[l]) i++;
            Swap(arr,i,j);
        }
        Swap(arr,l,i);
        if(i > k) return QuickSort(arr,k,0,i - 1);
        if(i < k) return QuickSort(arr,k,i + 1,arr.length - 1);
        return Arrays.copyOf(arr,k);
    }

    public void Swap(int[]arr,int a,int b){
        int temp = arr[a];
        arr[a] = arr[b];
        arr[b] = temp;
    }
}
```

