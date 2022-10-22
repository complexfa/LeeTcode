#### [剑指 Offer 07. 重建二叉树](https://leetcode.cn/problems/zhong-jian-er-cha-shu-lcof/)

#### 输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

#### 假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

this.preorder = preorder 表示传给当前对象地址

i表示根节点在inorder中的索引

root表示前序遍历的根节点

left表示中序遍历该节点左边界

right 表示中序遍历该结点右边界

root	left	right
左子树	root + 1	left	i -1
右子树	root + i - left + 1	i + 1 	right



```
/**

 * Definition for a binary tree node.

 * public class TreeNode {

 *    int val;

 *    TreeNode left;

 *    TreeNode right;

 *    TreeNode(int x) { val = x; }

 * }
   */
   class Solution {
   int[] preorder;
   Map<Integer,Integer> map = new HashMap<>();
   public TreeNode buildTree(int[] preorder, int[] inorder) {
       this.preorder = preorder;
       for(int i = 0; i < inorder.length; i++){
           map.put(inorder[i] , i);
       }
       return recur(0,0,inorder.length-1);
   }
   TreeNode recur(int root , int left, int right){
       if(left > right) return null;
       TreeNode node = new TreeNode(preorder[root]);
       int i = map.get(preorder[root]);
       node.left = recur(root + 1, left , i - 1 );
       node.right = recur( i - left + root + 1 , i + 1 , right);
       return node;

   }
   }
```