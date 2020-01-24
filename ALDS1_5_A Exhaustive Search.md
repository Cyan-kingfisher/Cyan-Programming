***description***<br>

Write a program which reads a sequence A of n elements and an integer M, and outputs "yes" if you can make M by adding elements in A, otherwise "no". You can use an element only once.

You are given the sequence A and q questions where each question contains Mi.

***Input***<br>
In the first line n is given. In the second line, n integers are given. In the third line q is given. Then, in the fourth line, q integers (Mi) are given.

***Output***<br>
For each question Mi, print yes or no.

***Constraints***<br>
n ≤ 20
q ≤ 200
1 ≤ elements in A ≤ 2000 
1 ≤ Mi ≤ 2000
***Sample Input 1***<br>
5
1 5 7 10 21
8
2 4 17 8 22 21 100 35
***Sample Output 1***<br>
no
no
yes
yes
yes
yes
no
no
***Notes***<br>
You can solve this problem by a Burte Force approach. Suppose solve(p, t) is a function which checkes whether you can make t by selecting elements after p-th element (inclusive). Then you can recursively call the following functions:

solve(0, M)
solve(1, M-{sum created from elements before 1st element})
solve(2, M-{sum created from elements before 2nd element})
...

The recursive function has two choices: you selected p-th element and not. So, you can check solve(p+1, t-A[p]) and solve(p+1, t) in solve(p, t) to check the all combinations.

For example, the following figure shows that 8 can be made by A[0] + A[2].

***MyCode***<br>
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        n = in.nextInt();
        int[] ints = new int[n];
        for (int i = 0; i < ints.length; i++) {
            ints[i] = in.nextInt();
        }
        int q = in.nextInt();
        while (q-- != 0){
            boolean bool = search(ints,0,0,in.nextInt());
            System.out.printf("%s\n",bool?"yes":"no");
        }
    }
    private static int i ;
    private static int n ;
    private static boolean search(int[] ints,int i,int sum,int key){
        if (key == sum)
            return true;
        if (i == n)
            return false;
        if(search(ints,i+1,sum+ints[i],key))
            return true;
        if (search(ints,i+1,sum,key))
            return true;
        return false;
    }
}

```