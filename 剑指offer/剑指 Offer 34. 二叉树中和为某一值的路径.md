### [剑指 Offer 34. 二叉树中和为某一值的路径](https://leetcode.cn/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

#### 题目：

给你二叉树的根节点 root 和一个整数目标和 targetSum ，找出所有 从根节点到叶子节点 路径总和等于给定目标和的路径。

叶子节点 是指没有子节点的节点。

```
示例 1：
输入：root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
输出：[[5,4,11,2],[5,8,4,5]]
示例 2：
输入：root = [1,2,3], targetSum = 5
输出：[]
示例 3：
输入：root = [1,2], targetSum = 0
输出：[]
```

#### 思路：回溯

通过先序遍历和记录路径

```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    List<List<Integer>> res = new ArrayList<>();
    LinkedList<Integer> path = new LinkedList<>();
    public List<List<Integer>> pathSum(TreeNode root, int target) {
          recur(root,target);
          return res;
    }
    public void recur(TreeNode root,int target){
        if(root == null) return;
        //已经到叶子节点
        path.add(root.val);
        target -= root.val;
        if(target == 0 && root.left == null && root.right == null)
        //当和为目标值并且已经遍历到叶子节点时加入结果集
        res.add(new LinkedList(path));
        //注意：加入时需要通过深拷贝，如果直接加入path会改变值，因为此时加入的是地址
        recur(root.left,target);
        //查找左子节点
        recur(root.right,target);
        //查找右子节点
        path.removeLast();
        //回溯
    }
}
```

