#### [剑指 Offer 18. 删除链表的节点](https://leetcode.cn/problems/shan-chu-lian-biao-de-jie-dian-lcof/)

#### 给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点。

#### 返回删除后的链表的头节点。

解题步骤：

1.如果头节点的值等于要搜索值，那么直接return head.next

2.pre = head cur = pre.next

3.一直循环知道cur为空，判断cur.value是否等于搜索值，如果不等于将指针向后挪，继续搜索，如果等于，删除该节点

4.返回头节点 

 * ```
 /**

     * Definition for singly-linked list.
     * public class ListNode {
     * int val;
     * ListNode next;
     * ListNode(int x) { val = x; }
     * }
       */
       class Solution {
       public ListNode deleteNode(ListNode head, int val) {
             ListNode pre = head;
             if(head.val == val) return head.next;
             ListNode cur = pre.next;
             while(cur != null){
           if(cur.val == val){
               pre.next = cur.next;
           }
           pre = cur;
            cur = cur.next; 
          } 
          return head;
    }
    }
 ```
 
 