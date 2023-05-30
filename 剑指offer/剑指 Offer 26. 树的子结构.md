### [剑指 Offer 26. 树的子结构](https://leetcode.cn/problems/shu-de-zi-jie-gou-lcof/)

#### 题目：

输入两棵二叉树A和B，判断B是不是A的子结构。(约定空树不是任意一个树的子结构)

B是A的子结构， 即 A中有出现和B相同的结构和节点值。

    例如:
    给定的树 A:
         3
        / \  
       4   5
      / \
     1   2
    给定的树 B：
       4 
      /
     1
    返回 true，因为 B 与 A 的一个子树拥有相同的结构和节点值。
    
    示例 1：
    输入：A = [1,2,3], B = [3,1]
    输出：false
    示例 2：
    输入：A = [3,4,5,1,2], B = [4,1]
    输出：true
####  思路：先序遍历

1.先序遍历A树的根节点

2.判断该根节点的子树是否与B树是相同的结构和节点值

isSubStructure(TreeNode A, TreeNode B) ：

B是A子结构的情况三种其一则返回true：A根节点的子树包含B；B是A左子树的子结构；B是A右子树的子结构

recur(TreeNode A,TreeNode B)：
B为空时说明B已经遍历完成，是A树的子结构

A为空或者A，B的值不一样时，说明B树不是A的子结构

否则遍历AB的左子节点，遍历AB的右子节点。

```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isSubStructure(TreeNode A, TreeNode B) {
         if(A == null ||B == null) return false;
         if(recur(A,B) || isSubStructure(A.left,B) || isSubStructure(A.right,B)) return true;
         return false;
    }

    public boolean recur(TreeNode A,TreeNode B){
        if(B == null) return true;
        if(A == null || A.val != B.val) return false;
        return recur(A.left,B.left) && recur(A.right,B.right);
      
    }
}
```

