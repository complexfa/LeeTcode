### [剑指 Offer 27. 二叉树的镜像](https://leetcode.cn/problems/er-cha-shu-de-jing-xiang-lcof/)

#### 题目：

请完成一个函数，输入一个二叉树，该函数输出它的镜像。

例如输入：

         4
       /   \
      2     7
     / \   / \
    1   3 6   9

镜像输出：

         4
       /   \
      7     2
     / \   / \
    9   6 3   1
#### 思路：递归

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
    public TreeNode mirrorTree(TreeNode root) {
         mirror(root);
         return root;
    }
    public void mirror(TreeNode t){
        if(t == null) return;  
        if(t.left != null) mirror(t.left);
        if(t.right != null) mirror(t.right);
        TreeNode temp = t.left;
        t.left = t.right;
        t.right = temp;
    }
}
```

