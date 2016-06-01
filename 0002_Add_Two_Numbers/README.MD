#Add Two Numbers
---------------------
>有2个用`链表形式`表示的`非负整数`，链表中的每个元素的val都是数字的某个位置上的数字，`链表中各元素的链接顺序和数字的显示顺序是相反的`。现在需要将2个数字相加，并将和以同样的链表方式返回。

>You are given two **linked lists** representing two **non-negative** numbers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

**Example：**
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```


**思路：**
>采用数学中**加法**的运算法则，将各位的值进行相加，如果存在进位，需要将进位加到下一位中。	


**代码：**
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
