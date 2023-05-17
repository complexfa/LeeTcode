### [剑指 Offer 28. 对称的二叉树](https://leetcode.cn/problems/dui-cheng-de-er-cha-shu-lcof/)

#### 题目：

请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

        1
       / \
      2   2
     / \ / \
    3  4 4  3

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

       1
      / \
      2   2
       \   \
       3    3
#### 思路：递归

第一想法是先镜像然后进行树的比较。

因为对称，通过比较子树的左右子树确定。

                  1
                 / \
             L  2   2 R
               / \ / \
        L.left3  4 4  3R.right
 

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
    public boolean isSymmetric(TreeNode root) {
        if(root == null) return true;
        else
          return  symmetry(root.left,root.right);

    }
    public boolean symmetry(TreeNode left,TreeNode right){
        if(left == null && right == null) return true;
        if(left == null || right == null ||left.val != right.val) return false;
        return symmetry(left.left,right.right) && symmetry(left.right,right.left);
    }
}
```

