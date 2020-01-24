***Description***
给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

    1
   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

    1
   / \
  2   2
   \   \
   3    3
***MyCode***
```java
Class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root==null)return true;
        return isSample(root.left,root.right);
    }
    private boolean isSample(TreeNode p, TreeNode q){
        if (p==null&&q==null)return true;
        if (p==null||q==null)return false;
        if(p.val!=q.val)return false;
        return isSample(p.left,q.right)&&isSample(p.right,q.left);
    }
}