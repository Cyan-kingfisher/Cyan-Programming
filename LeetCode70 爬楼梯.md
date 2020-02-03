***Description***

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。
每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？
注意：给定 n 是一个正整数。

示例 1：

>输入： 2
>输出： 2
>解释： 有两种方法可以爬到楼顶。
>1.  1 阶 + 1 阶
>2.  2 阶

示例 2：

>输入： 3
>输出： 3
>解释： 有三种方法可以爬到楼顶。
>1.  1 阶 + 1 阶 + 1 阶
>2.  1 阶 + 2 阶
>3.  2 阶 + 1 阶

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/climbing-stairs

***MyCode***
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix.length == 0)return false;
        leng_col = matrix[0].length;
        this.target = target;
        return search(matrix,0,matrix.length*leng_col-1);
    }
    private int leng_col ;
    private int target;
    private boolean search(int[][] matrix,int left,int right){
        if (left>right)return false;
        int mid = ( left + right ) /2;
        int row = mid / leng_col;
        int col = mid % leng_col;
        if (matrix[row][col]==target)return true;
        return search(matrix, left, mid-1)||search(matrix, mid+1, right);
    }
}