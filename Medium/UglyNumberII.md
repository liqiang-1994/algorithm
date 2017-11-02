



```
public class Solution {
    /*
     * @param n: An integer
     * @return: the nth prime number as description.
     */
    public int nthUglyNumber(int n) {
        if(n<=0) return 0;
        List<Integer> list = new ArrayList<>();
        list.add(1);
        int a=0, b=0, c=0;
        while(list.size()<n){
            int min = Math.min(list.get(a)*2,Math.min(list.get(b)*3, list.get(c)*5));
            list.add(min);
            if(list.get(a)*2==min) a++;
            if(list.get(b)*3==min) b++;
            if(list.get(c)*5==min) c++;
        }
        return list.get(list.size()-1);
    }
}
```