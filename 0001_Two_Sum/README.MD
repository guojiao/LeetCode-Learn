#Two Sum
---------------------
>��һ��ֻ����`���Σ�Integer��`�������У��������֮�͵���ָ����ֵ��2�������������е�������

>Given an array of **integers**, return indices of the two numbers such that they add up to a specific target.

**˼·��**
>�����������飬�ڻ�ȡָ����ֵaʱ�������������Ƿ��з���`a+b=c`��b��ֵ��

���巽���У�
- **����2��ѭ��**
	
	**���룺**
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

-	**����1��ѭ��+HashTable�ķ�ʽ`���Ƽ���`**
   HashTable�洢����Ҫ���ҵ�`b`ֵ�Ͷ�Ӧ��`a`�������index��
   ```flow
   st=>start: ��ʼ
   e=>end: ����
   op=>operation:  a=array[i]
   sub=>operation:  add  b and a'index to hashtable
	cond=>condition:  a in hashtable

	st->op->cond
	cond(yes)->e
	cond(no)->sub(right)->op
	
   ```

**���룺**
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