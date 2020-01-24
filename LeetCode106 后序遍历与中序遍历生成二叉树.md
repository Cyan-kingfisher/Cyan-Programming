***Description***<br>
 根据一棵树的中序遍历与后序遍历构造二叉树。

 注意:
 你可以假设树中没有重复的元素。

 例如，给出

 中序遍历 inorder = [9,3,15,20,7]
 后序遍历 postorder = [9,15,7,20,3]
 返回如下的二叉树：

    3
   / \
  9  20
 /  \
15   7
***MyCode***<br>
```java
import java.util.*;
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {
    Map<Integer,Integer> map;
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        map = new HashMap<>();
        for (int i = 0; i < inorder.length; i++) {
            map.put(inorder[i],i);
        }
        return Help(inorder,0,inorder.length,postorder,0,postorder.length);
    }
    private TreeNode Help(int[] inorder,int i_start,int i_end,int[] postoder,int p_start,int p_end){
        if(i_start==i_end)return null;
        int root_val = postoder[p_end-1];
        int root_index = map.get(root_val);
        TreeNode root = new TreeNode(root_val);
        root.left = Help(inorder,i_start,root_index,postoder,p_start,p_start+root_index-i_start);
        root.right = Help(inorder,root_index+1,i_end,postoder,p_start+root_index-i_start,p_end-1);
        return root;
    }
}

