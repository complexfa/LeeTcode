#### [剑指 Offer 06. 从尾到头打印链表](https://leetcode.cn/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

#### 输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

```
/**

 * Definition for singly-linked list.

 * public class ListNode {

 *    int val;

 *    ListNode next;

 *    ListNode(int x) { val = x; }

 * }
   */
   class Solution {
   public int[] reversePrint(ListNode head) {
     Stack<ListNode> stack = new Stack<>();
     ListNode temp = head;
       while (temp != null) {
           stack.push(temp);
           temp = temp.next;
       }

       int size = stack.size();//要记录size的值，因为stack 是一直不断改变的
       int[] print = new int[stack.size()];
       for(int i = 0 ;i < size ; i++){
         print[i] = stack.pop().val;

     }
      return print;
         }
   }
```

