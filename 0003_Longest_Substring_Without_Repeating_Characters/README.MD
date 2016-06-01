#Longest Substring Without Repeating Characters
---------------------
>从给定的字符串中获取`最长的`、`没有重复字符`的子串的长度

>Given a string, find the length of the **longest** substring **without repeating characters**.

**Examples:**
```
1 Given "abcabcbb", the answer is "abc", which the length is 3.
2 Given "bbbbb", the answer is "b", with the length of 1.
3 Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**思路：**
>与0001_Add_Sum的大体思路差不多。都是采用hashtable缓存需要的值，只不过这次是将每个字符在重复的时候要访问的下一个字符的index进行了存储。
	>- 查看当前字符是否在hashtable表中，如果在说明该字符存在重复，将hashtable中保存的当前字符的下一个字符的索引赋值给i: 	
	`i = Math.max(indexMap[s.charAt(j)+'']||0, i);`
	>- 如果当前字符不在hashtable表中, 则保持i的值不变。
	>- 获取j到i的长度，并和当前已知的最长的子串的长度进行比较，取最长进行更新。
	>- j++。重复上述操作


**代码：**
```javascript
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    var i=0,
        j=0,
        ln = s.length,
        indexMap = {},
        maxLen=0;
    while(j<ln){
        i = Math.max(indexMap[s.charAt(j)+'']||0, i);
        maxLen = Math.max(maxLen, j-i + 1);
        indexMap[s.charAt(j)+''] = j+1;
        j++;
    }
    return maxLen;
};
```
