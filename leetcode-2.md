<p>给出两个&nbsp;<strong>非空</strong> 的链表用来表示两个非负的整数。其中，它们各自的位数是按照&nbsp;<strong>逆序</strong>&nbsp;的方式存储的，并且它们的每个节点只能存储&nbsp;<strong>一位</strong>&nbsp;数字。</p>

<p>如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。</p>

<p>您可以假设除了数字 0 之外，这两个数都不会以 0&nbsp;开头。</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>(2 -&gt; 4 -&gt; 3) + (5 -&gt; 6 -&gt; 4)
<strong>输出：</strong>7 -&gt; 0 -&gt; 8
<strong>原因：</strong>342 + 465 = 807
</pre>

链接：https://leetcode-cn.com/problems/add-two-numbers/

答案：
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    ListNode node=null;
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        
        l1.val+=l2.val;
        //遍历l1链表确保每一个节点的值都在0-9之间
        ListNode flag=l1;
        while(flag.val>=10){
            flag.val-=10;
            if(flag.next==null){
            flag.next=new ListNode(0);
            
            }
            flag.next.val+=1;
            flag=flag.next;
        }
        //判断边界
        if(l1.next==null&&l2.next==null)return l1;
        else if(l1.next==null){
            ListNode ll1=new ListNode(0);
            l1.next=ll1;
        }
        else if(l2.next==null)return l1;
        addTwoNumbers(l1.next,l2.next);
        return l1;
    }
}
```
