# 最长回文子串

> 难度：中等
https://leetcode.cn/problems/longest-palindromic-substring/

<details>
    <summary>Tags</summary>
    <pre><code>string | dynamic-programming</code></pre>
</details>

## 题目
给你一个字符串 s，找到 s 中最长的回文子串。

### 示例
##### 示例 1：
```sh
输入：s = "babad"
输出："bab"
解释："aba" 同样是符合题意的答案。
```

##### 示例 2：
```sh
输入：s = "cbbd"
输出："bb"
```

### 提示：
- 1 <= s.length <= 1000
- s 仅由数字和英文字母组成

### 解法：
```
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
    let n = s.length;
    let res = '';
    let dp = Array.from(new Array(n),() => new Array(n).fill(false));
    for(let i = n-1;i >= 0;i--){
        for(let j = i;j < n;j++){
            dp[i][j] = s[i] == s[j] && (j - i < 2 || dp[i+1][j-1]);
            if(dp[i][j] && j - i +1 > res.length){
                res = s.substring(i,j+1);
            }
        }
    }
    return res;
};
```