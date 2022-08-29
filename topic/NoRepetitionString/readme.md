# 无重复字符的最长子串

> 难度：中等
https://leetcode.cn/problems/longest-substring-without-repeating-characters/

<details>
    <summary>Tags</summary>
    <pre><code>hash-table | two-pointers | string | sliding-window</code></pre>
</details>

## 题目
给定一个字符串 s ，请你找出其中不含有重复字符的 最长子串 的长度。

### 示例
##### 示例 1：
```sh
输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

##### 示例 2:
```sh
输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

##### 示例 3:
```sh
输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

### 提示：
- 0 <= s.length <= 5 * 104
- s 由英文字母、数字、符号和空格组成

### 解法
```
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    if (s.length <= 1) return s.length
    let maxLength = 1
    let temp = s[0]
    for (let i = 1; i < s.length; i++) {
        const index = temp.indexOf(s[i])
        if (index >= 0) {
            maxLength = Math.max(maxLength, temp.length)
            temp = temp.substring(index + 1)
            temp += s[i]
        } else {
            temp += s[i]
        }
    }
    maxLength = Math.max(maxLength, temp.length)
    return maxLength
};
```