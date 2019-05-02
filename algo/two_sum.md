# 找到数组中和为给定值的两个数

## 问题

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

**示例:**

> 给定 nums = [2, 7, 11, 15], target = 9
> 因为 nums[0] + nums[1] = 2 + 7 = 9
> 所以返回 [0, 1]

## 解答

LeetCode 有题解和分析, 参看[LeetCode](https://leetcode-cn.com/problems/two-sum/solution/)

使用一个 `HashMap` 保存数组, key为数组元素值, value为其下标. 然后循环数组并为map填充, 在填充之前判定 target-num[i] 的值是否在map中存在, 存在则匹配到了需要的值. 并从map中取到其下标. 

因为只遍历一次, 所以时间复杂度和空间复杂度均为 O(n) .

## 代码

```java
public class TowSum {

    public int[] twoSum(int[] nums, int target) {
        if (nums==null||nums.length<2){
            return new int[]{-1,-1};
        }
        int [] rs = new int[]{-1,-1};

        Map<Integer,Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(target-nums[i])){
                rs[0] = map.get(target-nums[i]);
                rs[1] = i;
                break;
            }
            map.put(nums[i],i);
        }

        return rs;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{2,5,8,7,9,4};
        int [] rs = new TowSum().twoSum(nums,17);
        System.out.println(Arrays.toString(rs));
    }
}
```