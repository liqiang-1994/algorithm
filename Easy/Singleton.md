### 单例
单例是最为常见的设计模式之一。对于任何时刻，如果某个类只存在且最多存在一个具体的实例，那么我们称这种设计模式为单例。
你的任务是设计一个getInstance方法，对于给定的类，每次调用getInstance时，都可以得到同一个实例。

```
class Solution {
    /**
     * @return: The same instance of this class every time
     */
    public static Solution getInstance() {
        return Single.INSTANCE;
    }
    private static class Single {
        private static final Solution INSTANCE = new Solution();
    }
}
```