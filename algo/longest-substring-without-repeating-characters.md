# 找到字符串中最长的非重复子串

## 问题

给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

**示例 1:**

> 输入: "abcabcbb"
> 输出: 3 
> 解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

**示例 2:**

> 输入: "bbbbb"
> 输出: 1
> 解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

**示例 3:**

> 输入: "pwwkew"
> 输出: 3
> 解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。

请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。

## 解答

使用滑动窗口思路. 已知子串长度为n, 窗口开始位置为i=0, 结束位置为j=0,使用一个集合存储字符元素, 循环字符串(j++), 当集合中存在字符时说明出现了重复子串, 此时的非重复串长度为j-i, 同时开始位置移动(i++);

仅需要做一次遍历, 时间复杂度为O(n).

## 代码

使用HashMap. 

```java
public static int lengthOfLongestSubString(String s) {
    if (s == null || s.length() == 0) {
        return 0;
    }
    int rs =0;
    int left = 0;
    HashMap<Character,Integer> map = new HashMap<>();
    for (int i = 0; i < s.length(); i++) {
        if (map.containsKey(s.charAt(i))){
            left = Math.max(left,map.get(s.charAt(i))+1);
        }
        map.put(s.charAt(i),i);
        rs = Math.max(rs,i+1-left);
    }
    return rs;
}
```

使用HashSet

```java
public static int lengthOfLongestSubStringSet(String s) {
    if (s == null || s.length() == 0) {
        return 0;
    }
    int rs = 0, i = 0, j = 0;
    int length = s.length();
    HashSet<Character> set = new HashSet<>();
    while (i < length && j < length) {
        if (!set.contains(s.charAt(j))){
            set.add(s.charAt(j));
            j++;
            rs = Math.max(rs,j-i);
        }else{
            set.remove(s.charAt(i));
            i++;
        }
    }
    System.out.println(set);
    return rs;
}
```

