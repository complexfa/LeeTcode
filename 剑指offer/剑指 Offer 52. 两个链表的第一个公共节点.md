### [剑指 Offer 52. 两个链表的第一个公共节点](https://leetcode.cn/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

#### 题目：

输入两个链表，找出它们的第一个公共节点。

如下面的两个链表：

|      | a1   | a2   |      |      |      |
| ---- | ---- | ---- | ---- | ---- | ---- |
|      |      |      | c1   | c2   | c3   |
| b1   | b2   | b3   |      |      |      |

在节点 c1 开始相交。

示例 1：

|      | 4    | 1    |      |      |      |
| ---- | ---- | ---- | ---- | ---- | ---- |
|      |      |      | 8    | 4    | 5    |
| 5    | 0    | 1    |      |      |      |

输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Reference of the node with value = 8
输入解释：相交节点的值为 8 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。

#### 思路：

假设a链表长度为a,b链表长度为b，相交节点长度为c，A中相交前有a-c个节点，B中相交前有b-c个节点。

指针A先遍历A链表再遍历B链表相交前的部分为a+b-c

指针B先遍历B链表再遍历A链表相交前的部分为b+a-c

此时他们正好相交

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
class Solution {
    ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode A = headA;
        ListNode B = headB;
        while(A!=B){
            A = A != null ?A.next:headB;
            B = B != null ?B.next:headA;
        }
        return A;
    }
}
```

