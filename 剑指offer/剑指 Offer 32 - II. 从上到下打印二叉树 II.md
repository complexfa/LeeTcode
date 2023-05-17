### [剑指 Offer 32 - II. 从上到下打印二叉树 II](https://leetcode.cn/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

#### 题目：

从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行。

例如:
给定二叉树: [3,9,20,null,null,15,7],

        3
       / \
      9  20
        /  \
       15   7

返回其层次遍历结果：

[[3],[9,20], [15,7]]

#### 思路：递归

当根节点变为null时，说明已经遍历完毕

当总数组大小等于深度时，说明需要新建一个数组存放本层的数据

添加根节点的数组

再一层层遍历根节点的左右节点

Queue的API

| 变量和类型 | 方法         | 描述                                                         |
| ---------- | ------------ | ------------------------------------------------------------ |
| `boolean`  | `add(E e)`   | 如果可以在不违反容量限制的情况下立即执行此操作，则将指定的元素插入此队列，成功时返回 `true`  ，如果当前没有空间，则抛出 `IllegalStateException` 。 |
| `E`        | `element()`  | 检索但不删除此队列的头部。                                   |
| `boolean`  | `offer(E e)` | 如果可以在不违反容量限制的情况下立即执行此操作，则将指定的元素插入此队列。 |
| `E`        | `peek()`     | 检索但不删除此队列的头部，如果此队列为空，则返回 `null` 。   |
| `E`        | `poll()`     | 检索并删除此队列的头部，如果此队列为空，则返回 `null` 。     |
| `E`        | `remove()`   | 检索并删除此队列的头部。                                     |

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
    List<List<Integer>> res= new ArrayList<>();
    public List<List<Integer>> levelOrder(TreeNode root) {
      dfs(0,root);
      return res;
    }
    public void dfs(int depth,TreeNode root){
        if(root == null) return;
        if(res.size() == depth){
            res.add(new ArrayList());
        }
        res.get(depth).add(root.val);
        dfs(depth + 1,root.left);
        dfs(depth + 1,root.right);
    }
}
```

