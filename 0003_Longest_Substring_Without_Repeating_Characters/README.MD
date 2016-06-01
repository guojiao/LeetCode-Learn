#Longest Substring Without Repeating Characters
---------------------
>�Ӹ������ַ����л�ȡ`���`��`û���ظ��ַ�`���Ӵ��ĳ���

>Given a string, find the length of the **longest** substring **without repeating characters**.

**Examples:**
```
1 Given "abcabcbb", the answer is "abc", which the length is 3.
2 Given "bbbbb", the answer is "b", with the length of 1.
3 Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

**˼·��**
>��0001_Add_Sum�Ĵ���˼·��ࡣ���ǲ���hashtable������Ҫ��ֵ��ֻ��������ǽ�ÿ���ַ����ظ���ʱ��Ҫ���ʵ���һ���ַ���index�����˴洢��
	>- �鿴��ǰ�ַ��Ƿ���hashtable���У������˵�����ַ������ظ�����hashtable�б���ĵ�ǰ�ַ�����һ���ַ���������ֵ��i: 	
	`i = Math.max(indexMap[s.charAt(j)+'']||0, i);`
	>- �����ǰ�ַ�����hashtable����, �򱣳�i��ֵ���䡣
	>- ��ȡj��i�ĳ��ȣ����͵�ǰ��֪������Ӵ��ĳ��Ƚ��бȽϣ�ȡ����и��¡�
	>- j++���ظ���������


**���룺**
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