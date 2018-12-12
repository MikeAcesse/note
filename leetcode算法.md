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
  - 第一种：{ 1,2 ,3 ,4 }
  - 第二种：new int[2]。数组全是为0的位初始化数组长度位2
  - 第三种：new int[]{};[]内不能初始化数组长度，数组长度有{}元素决定

```java
// 方法一：暴力法（自己写的）
class Solution {
    public int[] twoSum(int[] nums, int target) {
        // int[] nums ={2,7,11,15};
    		for (int i=0;i<nums.length ;i++ ) {
    			// if(nums[i] > target)continue; 虽说这样可以减少循环次数，但在负数的情况下，这个判断就会抛出异常
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
    }
}


// 方法二（优秀答案）：两遍哈希表
//为了对运行时间复杂度进行优化，我们需要一种更有效的方法来检查数组中是否存在目标元素。如果存在，我们需要找出它的索引。保持数组中的每个元素与其索引相互对应的最好方法是什么？哈希表。
//通过以空间换取速度的方式，我们可以将查找时间从 O(n)O(n) 降低到 O(1)O(1)。哈希表正是为此目的而构建的，它支持以 近似 恒定的时间进行快速查找。我用“近似”来描述，是因为一旦出现冲突，查找用时可能会退化到 O(n)O(n)。但只要你仔细地挑选哈希函数，在哈希表中进行查找的用时应当被摊销为 O(1)O(1)。
//一个简单的实现使用了两次迭代。在第一次迭代中，我们将每个元素的值和它的索引添加到表中。然后，在第二次迭代中，我们将检查每个元素所对应的目标元素（target - nums[i]target−nums[i]）是否存在于表中。注意，该目标元素不能是 nums[i]nums[i] 本身！
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        map.put(nums[i], i);
    }
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement) && map.get(complement) != i) { //注意，元素不能重复
            return new int[] { i, map.get(complement) };
        }
    }
    throw new IllegalArgumentException("No two sum solution");
}
 // 方法三：一遍哈希表 。对折一半
 public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement)) {
            return new int[] { map.get(complement), i };
        }
        map.put(nums[i], i);
    }
    throw new IllegalArgumentException("No two sum solution");
}

```
 ---
# 537. 复数乘法
给定两个表示复数的字符串。

返回表示它们乘积的字符串。注意，根据定义 i2 = -1 。

示例 1:
``` java
输入: "1+1i", "1+1i"
输出: "0+2i"
解释: (1 + i) * (1 + i) = 1 + i2 + 2 * i = 2i ，你需要将它转换为 0+2i 的形式。
```
示例 2:
``` java
输入: "1+-1i", "1+-1i"
输出: "0+-2i"
解释: (1 - i) * (1 - i) = 1 + i2 - 2 * i = -2i ，你需要将它转换为 0+-2i 的形式。
```
注意:

输入字符串不包含额外的空格。

输入字符串将以 a+bi 的形式给出，其中整数 a 和 b 的范围均在 [-100, 100] 之间。输出也应当符合这种形式。

##### 我的解法：
*解题思路：*截取字符串中的，虚部和实部，然后进行运算 。注意i^2等于-1
``` java
class Solution {
   public String complexNumberMultiply(String fir, String sec) {
		Integer a = Integer.valueOf(fir.substring(0,fir.indexOf("+")));
		String bi = fir.substring(fir.indexOf("+")+1);
		Integer b = Integer.valueOf(bi.substring(0,bi.indexOf("i")));

		Integer c = Integer.valueOf(sec.substring(0,sec.indexOf("+")));
		String di = sec.substring(sec.indexOf("+")+1);
		Integer d = Integer.valueOf(di.substring(0,di.indexOf("i")));
		return String.format("%d+%di", a * c - b * d, a * d + b * c);
   }
}
```
##### 优秀解法：
``` java
public class Solution {
   public String complexNumberMultiply(String a, String b) {
       String x[] = a.split("\\+|i");
       String y[] = b.split("\\+|i");
       int a_real = Integer.parseInt(x[0]);
       int a_img = Integer.parseInt(x[1]);
       int b_real = Integer.parseInt(y[0]);
       int b_img = Integer.parseInt(y[1]);
       return (a_real * b_real - a_img * b_img) + "+" + (a_real * b_img + a_img * b_real) + "i";

   }
}
```
