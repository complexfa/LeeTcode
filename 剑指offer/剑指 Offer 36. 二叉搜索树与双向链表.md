### [剑指 Offer 36. 二叉搜索树与双向链表](https://leetcode.cn/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

#### 题目：

输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向。

为了让您更好地理解问题，以下面的二叉搜索树为例：

我们希望将这个二叉搜索树转化为双向循环链表。链表中的每个节点都有一个前驱和后继指针。对于双向循环链表，第一个节点的前驱是最后一个节点，最后一个节点的后继是第一个节点。

下图展示了上面的二叉搜索树转化成的链表。“head” 表示指向链表中有最小元素的节点。

####  思路：中序遍历+dfs

```
/*
// Definition for a Node.
class Node {
    public int val;
    public Node left;
    public Node right;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val,Node _left,Node _right) {
        val = _val;
        left = _left;
        right = _right;
    }
};
*/
class Solution {
    Node pre,head;
    public Node treeToDoublyList(Node root) {
         if(root == null) return null;
         dfs(root);
         head.left = pre;
         pre.right = head;
         //将头尾指针连接双向
         return head;
    }

    void dfs(Node cur){
        if(cur == null) return;
        //说明已经遍历到叶子节点
        dfs(cur.left); 
        cur.left = pre;
        //cur的左节点置为pre节点
        if(pre != null) pre.right = cur;
        //如果pre不为空，pre的右节点为cur
        else head = cur;
        //如果pre为空说明为最小元素的节点
        pre = cur;
        //建立联系后将cur移至pre的位置
        dfs(cur.right);

    }
}
```

