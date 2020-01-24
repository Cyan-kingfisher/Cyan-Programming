***Description***
给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）

例如：
给定二叉树 [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其自底向上的层次遍历为：

[
  [15,7],
  [9,20],
  [3]
]
***MyCode***
```java
import java.util.*;

public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }

}

class Solution {
    private List<List<Integer>> listlist;
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        listlist = new ArrayList<>();
        if (root==null)return listlist;
        Queue<TreeNode> queue = new ArrayDeque<>(50);
        queue.add(root);
        TreeNode in;
        List<Integer> list = new ArrayList<>(50);

        while (!queue.isEmpty()){
            int leng = queue.size();
            for (int i = 0; i < leng; i++) {
                in = queue.remove();
                if (in.left!=null)queue.add(in.left);
                if (in.right!=null)queue.add(in.right);
                list.add(in.val);
            }
            listlist.add(list);
            list = new ArrayList<>();
        }
        Collections.reverse(listlist);
        return listlist;
    }
}