# 1.两数之和


给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出 **和为目标值 ***`target`*  的那 **两个** 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。


<pre><strong>输入：</strong>nums = [2,7,11,15], target = 9
<strong>输出：</strong>[0,1]
<strong>解释：</strong>因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。
</pre>


```cpp
std::vector<int> TwoSum::twoSum(std::vector<int> &nums, int target) {
    std::unordered_map<int, int> map;
    for (int i=0; i< nums.size(); i++) {
        auto front = map.find(target - nums[i]);
        if (front != map.end()) {
            return {front->second, i};
        }
        map.insert(std::pair<int, int>(target - nums[i], i));
    }
    return {};
}
```
