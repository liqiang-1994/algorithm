### 旋转字符串
通过循环把左边的字符旋转到右边得到另一个单词称为旋转单词,计算一个列表里总共有多少个不同的旋转单词集。

```
Given dict = ["picture", "turepic", "icturep", "word", "ordw", "lint"]
return 3.

"picture", "turepic", "icturep" are same ratote words.
"word", "ordw" are same too.
"lint" is the third word that different from the previous two words.
```
* 通过重写equals和hashCode方法，使之改变对象相等的判断方法
```
public class Solution {
    /*
     * @param words: A list of words
     * @return: Return how many different rotate words
     */
     private String value;
     public Solution(){};
     public Solution(String value){
         this.value = value;
     }
     
      public boolean equals(Object o) {
        if(o==this){
            return true;
        }
        if(!(o instanceof Solution)) {
            return false;
        }
        Solution word=(Solution) o;
        return check(this.value,word.value);
    }
     public int hashCode() {
        List<Character> l=new ArrayList<Character>();
        for(char x:value.toCharArray()){
            l.add(x);
        }
        Collections.sort(l);
        StringBuilder b=new StringBuilder();
        for(char x:l){
            b.append(x);
        }
        return b.toString().hashCode();
    }
     public boolean check(String s1, String s2){
         //return (s1+s1).contains(s2);
         return s1.length()==s2.length() && (s1+s1).indexOf(s2)!=-1;
     }
     
     public int countRotateWords(List<String> words) {
         Set<Solution> set = new HashSet<>();
         for(String x : words){
             if(!set.contains(x)){
                 set.add(new Solution(x));
             }
         }
         return set.size();
     }
}
```