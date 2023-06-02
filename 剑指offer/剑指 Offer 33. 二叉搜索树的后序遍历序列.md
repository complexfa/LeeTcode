### [剑指 Offer 33. 二叉搜索树的后序遍历序列](https://leetcode.cn/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)

#### 题目：

输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同。

```
参考以下这颗二叉搜索树：
     5
    / \
   2   6
  / \
 1   3
示例 1：
输入: [1,6,3,2,5]
输出: false
示例 2：
输入: [1,3,2,6,5]
输出: true
```

#### 思路：辅助栈

根据二叉搜索树的性质可以看出左子节点是一棵子树中值最小的，通过反后序遍历，即先根节点再右节点再左节点，利用一个辅助栈，存放子树的根节点和右节点，当左节点小于他们时，说明该后序遍历结果正确。

```
class Solution {
    public boolean verifyPostorder(int[] postorder) {
        Stack<Integer> stack = new Stack<>();
        int root = Integer.MAX_VALUE;
        //初始值设为最大
        for(int i = postorder.length - 1;i >= 0;i--){
            if(postorder[i] > root) return false;
            while(!stack.empty() && postorder[i] < stack.peek())
            //当栈为不为空时并且遍历到的值小于栈顶值时弹出栈顶元素
            root = stack.pop();
            //当栈为空时，加入栈
            stack.push(postorder[i]);
        }
        //若遍历完成，说明该后序遍历数组符合二叉搜索树定义
        return true;
    }
}
```

