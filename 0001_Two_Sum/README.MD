#Two Sum
---------------------
>从一个只包含`整形（Integer）`的数组中，返回相加之和等于指定数值的2个数字在数组中的索引。

>Given an array of **integers**, return indices of the two numbers such that they add up to a specific target.

**思路：**
>遍历整个数组，在获取指定数值a时，查找数组中是否有符合`a+b=c`的b的值。

具体方案有：
- **采用2重循环**
	
	**代码：**
	```javascript
	/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    var result = [], diffNums = {};
    for(var i=0,ln = nums.length;i<ln;i++){
        for(var j=i+1;j<ln;j++){
	      if(nums[i]+nums[j] === target){
	          return result.concat(i,j);
	      }
        }
    }
    return result;
}
	```

-	**采用1重循环+HashTable的方式`（推荐）`**
   HashTable存储所有要查找的`b`值和对应的`a`在数组的index。
	- 将i位置的数值赋值给a： a = array[i]
	- 检测a是否是其他值要查找的满足`a+b=c`的差值b: hashtable[a] != undefined
	- 如果是，则返回a的index和hashtable中存储的key为a的value。
	- 如果不是，将a需要的b值和a的值以key和value的形式存储到hashtable中。
	- i++。重复上述步骤。


   ```flow
   st=>start: 开始
   e=>end: 结束
   op=>operation:  a=array[i]
   sub=>operation:  add  b and a'index to hashtable
	cond=>condition:  a in hashtable

	st->op->cond
	cond(yes)->e
	cond(no)->sub(right)->op
	
   ```

**代码：**
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    var result = [], diffNums = {};
    for(var i=0,ln = nums.length;i<ln;i++){
        var num = nums[i],
            diffNum = diffNums[num+''];
        if(diffNum || diffNum === 0){
            result = [diffNum, i];
            return result;
        }else{
            diffNums[target-num+''] = i;
        }
    }
    return result;
};
```
