***Description***
<br>
给定一个单链表，其中的元素按升序排序，将其转换为高度平衡的二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

示例:

给定的有序链表： [-10, -3, 0, 5, 9],

一个可能的答案是：[0, -3, 9, -10, null, 5], 它可以表示下面这个高度平衡二叉搜索树：

>         0
>        / \
>      -3   9
>      /   /
>    -10  5
>

<br>***MyCode***<br>
```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
class ListNode {
     int val;
     ListNode next;
     ListNode(int x) { val = x; }
 }
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}
class Solution {
    int leng;
    ListNode list;
    public TreeNode sortedListToBST(ListNode head) {
        leng = 0;
        list = head;
        while (head!=null){
            leng++;
            head = head.next;
       }
        return help( 0,leng);
    }
    private TreeNode help(int left,int right){
        if (left == right)return null;
        int mid = (left+right)/2;
        TreeNode LL = help(left,mid);
        TreeNode root = new TreeNode(list.val);
        list = list.next;
        root.left = LL;
        root.right = help(mid+1,right);
        return root;
    }
}