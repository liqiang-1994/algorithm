### 丑数
检测一个整数是不是丑数。丑数的定义是：只包含质因子2,3,5的正整数，比如6,8就是丑数，但是14不是丑数因为它包含质因子7.
```
可以认为1是一个特殊的丑数
给出 num = 8，返回 true。
给出 num = 14，返回 false。
```

```
public class Solution {
    /*
     * @param num: An integer
     * @return: true if num is an ugly number or false
     */
    public boolean isUgly(int num) {
        // write your code here
        while(num < 1) return false;
        num = next(num, 2);
        num = next(num, 3);
        num = next(num, 5);
        return num == 1;
    }

    public int next(int num, int n) {
        while(num%n==0) {
            num = num/n;
        }
        return num;
    }
}
```

```
public class Solution {
    /*
     * @param num: An integer
     * @return: true if num is an ugly number or false
     */
    public boolean isUgly(int num) {
        if(num < 1) return false;
        if(num == 1) return true;
        boolean two = false;
        boolean three = false;
        boolean five = false;
        if(num % 2 == 0){
            two = isUgly(num/2);
        }if(num % 3 == 0){
            three = isUgly(num/3);
        }if(num % 5 == 0){
            five = isUgly(num/5);
        }
        return (two || three || five);
    }
}
```