#Add Two Numbers
---------------------
>��2����`������ʽ`��ʾ��`�Ǹ�����`�������е�ÿ��Ԫ�ص�val�������ֵ�ĳ��λ���ϵ����֣�`�����и�Ԫ�ص�����˳������ֵ���ʾ˳�����෴��`��������Ҫ��2��������ӣ���������ͬ����������ʽ���ء�

>You are given two **linked lists** representing two **non-negative** numbers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

**Example��**
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```


**˼·��**
>������ѧ��**�ӷ�**�����㷨�򣬽���λ��ֵ������ӣ�������ڽ�λ����Ҫ����λ�ӵ���һλ�С�	


**���룺**
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
 
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    var result = new ListNode(0),
        current = result,
        ident = 0,
        p = l1,
        q = l2;
    while(p !== null || q!== null){
        var pValue = !!p?(p.val || 0):0,
            qValue = !!q?(q.val || 0):0,
            sum = pValue + qValue + ident;
            
            ident = (sum/10)|0;
            current.next = new ListNode(sum%10);
            current = current.next;
            p = p&&p.next;
            q = q&&q.next;
    }
    if(ident > 0){
        current.next = new ListNode(ident);
    }
    return result.next;
};
```