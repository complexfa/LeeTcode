### [剑指 Offer 24. 反转链表](https://leetcode.cn/problems/fan-zhuan-lian-biao-lcof/)

### 题目：

定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

###  思路：双指针

| 1->  | 2->  | 3->  | 4->  | null |
| ---- | ---- | ---- | ---- | ---- |
| cur  | temp |      |      | pre  |

| null | <-1  | 2->      | 3->  | 4    |
| ---- | ---- | -------- | ---- | ---- |
|      | pre  | cur,temp |      |      |

| null | <-1  | 2->  | 3->  | 4    |
| ---- | ---- | ---- | ---- | ---- |
|      | pre  | cur  | temp |      |

| null | <-1  | <-2  | 3->      | 4    |
| ---- | ---- | ---- | -------- | ---- |
|      |      | pre  | cur,temp |      |

| null | <-1  | <-2  | <-3  | 4    |
| ---- | ---- | ---- | ---- | ---- |
|      |      | pre  | cur  | temp |

| null | <-1  | <-2  | <-3  | 4        |
| ---- | ---- | ---- | ---- | -------- |
|      |      |      | pre  | cur,temp |

| null | <-1  | <-2  | <-3  | <-4  |
| ---- | ---- | ---- | ---- | ---- |
|      |      |      |      | pre  |

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
    public ListNode reverseList(ListNode head) {
        ListNode pre,cur,temp;
        pre = null;
        cur = head;
        while(cur != null){
            temp = cur.next;
            cur.next = pre;
            pre = cur;
            cur = temp;
        }
        return pre;
    }
}
```

