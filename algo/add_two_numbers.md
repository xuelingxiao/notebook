# 链表两数相加

## 问题

给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

**示例:**

> 输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
> 输出：7 -> 0 -> 8
> 原因：342 + 465 = 807

## 解答

我们使用变量来跟踪进位，并从包含最低有效位的表头开始模拟逐位相加的过程。

## 代码

```java
public class AddTwoNumbers {

    private class ListNode{
        int val;
        ListNode next;
        ListNode(int x){this.val=x;}
    }

    /**
     * 输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
     * 输出：7 -> 0 -> 8
     * 原因：342 + 465 = 807
     *
     * @param l1
     * @param l2
     * @return
     */
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode sumNode = new ListNode(0);
        ListNode p1=l1,p2=l2,curr = sumNode;
        int carry = 0;
        while (p1!=null||p2!=null){
            int x = p1==null?0:p1.val;
            int y = p2==null?0:p2.val;
            int sum = carry+x+y;
            carry = sum/10;
            curr.next = new ListNode(sum%10);
            curr = curr.next;
            if(p1!=null) p1 = p1.next;
            if(p2!=null) p2 = p2.next;
        }
        if (carry>0){
            curr.next = new ListNode(carry);
        }

        return  sumNode.next;
    }
}
```