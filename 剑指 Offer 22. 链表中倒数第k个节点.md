#### [剑指 Offer 22. 链表中倒数第k个节点](https://leetcode.cn/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

#### 题目：

输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。

例如，一个链表有 6 个节点，从头节点开始，它们的值依次是 1、2、3、4、5、6。这个链表的倒数第 3 个节点是值为 4 的节点。

#### 思路：双指针

为了避免k值较大链表较长的情况

* 设置former和latter指针先同时指向头节点
* 将latter先移动k个节点
* 当latter不为空时，将former和latter同时后移（即他们中间相隔k个节点）
* 返回former节点

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        ListNode former,latter;
        former = head;
        latter = head;
        for(int i = 0;i < k;i++){
            latter = latter.next;
        }
        while(latter!= null){
            latter = latter.next;
            former = former.next;
        }
        return former;
    }
}
```

