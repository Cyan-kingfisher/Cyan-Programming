***Description***

编写一个高效的算法来判断 m x n 矩阵中，是否存在一个目标值。该矩阵具有如下特性：

每行中的整数从左到右按升序排列。
每行的第一个整数大于前一行的最后一个整数。
示例 1:

输入:

>matrix = [
>[1,   3,  5,  7],
>[10, 11, 16, 20],
>[23, 30, 34, 50]
>]
>target = 3

输出: true
示例 2:

输入:

>matrix = [
>[1,   3,  5,  7],
>[10, 11, 16, 20],
>[23, 30, 34, 50]
>]
>target = 13

输出: false

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/search-a-2d-matrix/

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