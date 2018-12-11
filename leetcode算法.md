# 1、宝石与石头

给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

示例 1:
输入: J = "aA", S = "aAAbbbb"
输出: 3

示例 2:
输入: J = "z", S = "ZZ"
输出: 0

注意:
S 和 J 最多含有50个字母。
 J 中的字符不重复。

 ```java
 class Solution {
    public int numJewelsInStones(String J, String S) {
        int num = 0;
        char[] gems = J.toCharArray();
        char[] stones = S.toCharArray();
        for (int i = 0; i < gems.length; i++) {
            for (int k = 0; k < stones.length; k++) {
                if(gems[i] == stones[k])++num;
            }
        }
        return num;
    }
}
```

# 2、两数之和

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

错误：
 1. java中数组的定义，使用{}而不是[]。
 2. 忽略了数组的定义int[]
 3. 定义数组的方式：
```java
for (int i=0;i<nums.length ;i++ ) {
  // if(nums[i] > target)continue;（负数的情况下，这个判断就会抛出异常）
  for (int j=0;j<nums.length ;j++ ) {
    if (i<=j) continue;
    if ((nums[j] + nums[i]) == target) {
      int[] result = {0,0};
      result[0]=i;
      result[1]=j;
      return result;
    }
  }
}
return null;
```
