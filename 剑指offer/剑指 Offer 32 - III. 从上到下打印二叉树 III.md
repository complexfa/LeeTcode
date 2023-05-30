### [剑指 Offer 32 - III. 从上到下打印二叉树 III](https://leetcode.cn/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)

#### 题目：

请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推。

```
例如:
给定二叉树: [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：
[
  [3],
  [20,9],
  [15,7]
]
```

#### 思路：层序遍历+双端队列

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
    public List<List<Integer>> levelOrder(TreeNode root) {
          Queue<TreeNode> queue = new LinkedList<>();
          //单向队列
          List<List<Integer>> res = new ArrayList<>();
          //结果数组
          if(root != null) queue.add(root);
          while(!queue.isEmpty()){
              LinkedList<Integer> ans = new LinkedList<>();
              //ans作为双端队列
              //通过队列中元素的个数判断需要遍历几个节点
              for(int i = queue.size();i > 0;i--){
                    TreeNode node = queue.poll();//弹出队头元素
                    if(res.size() % 2 == 0) ans.addLast(node.val);
                    //res的大小从0开始，如果为0，说明是奇数层，应该从队尾添加元素
                    else ans.addFirst(node.val);
                    //不是0，说明是偶数层，应该从队头添加元素
                    if(node.left != null) queue.add(node.left);
                    //如果该节点左节点存在，加入单向队列
                    if(node.right != null) 
                    queue.add(node.right);
                    //如果该节点右节点存在，加入单向队列
              }
              res.add(ans);
          }
          return res;
    }
}
```

