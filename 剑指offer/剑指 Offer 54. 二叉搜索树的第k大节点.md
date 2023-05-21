### [剑指 Offer 54. 二叉搜索树的第k大节点](https://leetcode.cn/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

#### 题目：

给定一棵二叉搜索树，请找出其中第 k 大的节点的值。

```
示例 1:
输入: root = [3,1,4,null,2], k = 1
   3
  / \
 1   4
  \
   2
输出: 4
示例 2:
输入: root = [5,3,6,2,4,null,null,1], k = 3
       5
      / \
     3   6
    / \
   2   4
  /
 1
输出: 4
```

#### 思路：

二叉搜素树的中序遍历得到的是一个递增的序列，题目找第K大节点，即递减序列的第K个，所以可以通过中序遍历的倒序，先右节点再根节点再左节点。通过K值的减少可提前返回。

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
    int res,k;
    public int kthLargest(TreeNode root, int k) {
       this.k = k;
       dfs(root);
       return res;
    }
    public void dfs(TreeNode root){
        if(root == null) return;
        dfs(root.right);
        if(k == 0)  return;
        if(--k == 0){
            res = root.val; 
        } 
        dfs(root.left);
    }

}
```

