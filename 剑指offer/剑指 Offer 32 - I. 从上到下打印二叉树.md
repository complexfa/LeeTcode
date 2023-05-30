### [剑指 Offer 32 - I. 从上到下打印二叉树](https://leetcode.cn/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

#### 题目：

上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印。

    例如:
    给定二叉树: [3,9,20,null,null,15,7], 
        3
       / \
      9  20
        /  \
       15   7
    返回：
    [3,9,20,15,7]
#### 思路：队列+层序遍历

通过队列先入先出的特点进行层序遍历

Queue时尽量使用offer()加入元素，poll()移出元素

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
    public int[] levelOrder(TreeNode root) {
        if(root == null) return new int[]{};
        ArrayList<Integer> res = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            TreeNode node = queue.poll();
            res.add(node.val);
            if(node.left != null) queue.add(node.left);
            if(node.right != null) queue.add(node.right);
        }
        int[] ans = new int[res.size()];
        for(int i = 0;i < res.size();i++){
            ans[i] = res.get(i);
        }
        return ans;
    }
}
```

