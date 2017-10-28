### 二叉树的路径和

给定一个二叉树，找出所有路径中各节点相加总和等于给定目标值的路径。
一个有效的路径，指的是从根节点到叶节点的路径。

```
给定一个二叉树，和目标值 = 5;

     1
    / \
   2   4
  / \
 2   3

返回：

[
  [1, 2, 2],
  [1, 4]
]

```

```
/**
 * Definition of TreeNode:
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left, right;
 *     public TreeNode(int val) {
 *         this.val = val;
 *         this.left = this.right = null;
 *     }
 * }
 */


public class Solution {
    /*
     * @param root: the root of binary tree
     * @param target: An integer
     * @return: all valid paths
     */
    public List<List<Integer>> binaryTreePathSum(TreeNode root, int target) {

        List<List<Integer>> result = new ArrayList<>();
        if(root == null) return result;
        Stack<Integer> stack = new Stack<>();
        binaryTreePathSumHelp(result,stack, root,0,target);
        return result;
    }
    public void binaryTreePathSumHelp(List<List<Integer>> result, Stack<Integer> stack, TreeNode root, int sum, int target) {
        sum += root.val;
        stack.push(root.val);
        if(sum==target && root.left==null && root.right==null) {
            result.add(new ArrayList<>(stack));
            stack.pop();
            return;
        } else {
            if(root.left != null) {
                binaryTreePathSumHelp(result, stack, root.left, sum, target);
            } if(root.right != null) {
                binaryTreePathSumHelp(result, stack, root.right, sum, target);
            }
            stack.pop();//递归返回时要弹出栈首的元素，不管是否找到
        }
    }
}
```