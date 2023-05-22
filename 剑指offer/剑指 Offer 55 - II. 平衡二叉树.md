### [剑指 Offer 55 - II. 平衡二叉树](https://leetcode.cn/problems/ping-heng-er-cha-shu-lcof/)

#### 题目：

输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树。

示例 1:

给定二叉树 [3,9,20,null,null,15,7]

        3
       / \
      9  20
        /  \
       15   7

返回 true 。

示例 2:

给定二叉树 [1,2,2,3,3,null,null,4,4]

           1
          / \
         2   2
        / \
       3   3
      / \
     4   4
    返回 false 。
#### 思路：从底至上+剪枝

对二叉树进行后续遍历，返回各子树的深度max(left，right) + 1，同时判断是否平衡，如果不平衡返回-1，如果子树为不平衡，那么直接返回。

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
    public boolean isBalanced(TreeNode root) {
     if(depth(root) != -1) return true;
     else return false;
    }
    public int depth(TreeNode root)   {
      if(root == null) return 0;
      int left = depth(root.left);
      int right = depth(root.right);
      if(left == -1 || right == -1)
      return -1;
      return Math.abs(left - right) < 2 ? Math.max(left , right) + 1:-1;
    }
}
```

