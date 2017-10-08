### 斐波那契数列

查找斐波那契数列中第N个数。
所谓的斐波那契数列是指：
* 前两个数是0和1。
* 第i个数是第i-1个数和第i-2个数的和。

斐波纳契数列的前10个数字是：
0, 1, 1, 2, 3, 5, 8, 13, 21, 34 ...

```
public class Solution {
     /*
     * @param n: an integer
     * @return: an ineger f(n)
     */
     public int fibonacci(int n) {
         if (n==1) {
             return 0;
         }if (n==2 || n==3) {
             return 1;
         }
         int i = 4;
         int s1 = 1;
         int s2 = 1;
         int sum = 0;
         while(i<=n) {
             sum = s1 + s2;
             s1 = s2;
             s2 = sum;
             i++;
         }
         return sum;
     }
}
```