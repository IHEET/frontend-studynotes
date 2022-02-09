# frontend-studynotes

2022.02.09

做【复制带随机指针的链表】遇到了问题：用迭代法解决，在第一次迭代复制所有值节点后，进行第二次迭代，一次性将复制节点的random和next指向正确的位置出现问题。代码如下：

```
var copyRandomList = function(head) {
    var p = head,q;
    while(p != null) {
        q = new Node(p.val);
        q.next = p.next;
        p.next = q;
        p = q.next;
    }
    
    var newHead =  head.next;
    var q = newHead, p = head;
    while(q != null) {
        q.random = (p.random != null ? p.random.next : null);
        if(p.next != null) {
            p.next = p.next.next;
        }
        p = p.next;
        if(q.next != null) {
            q.next = q.next.next;
        }
        q = q.next;
           
    }
    return newHead;//Random pointer of node with label 13 points to a node from the original list.
};
```



2022.02.08

[86. 分隔链表](https://juejin.cn/post/7062390809768755208/)

2022.02.03

[19.删除链表的倒数第 N 个结点](https://juejin.cn/post/7060335574632267813/)

[83. 删除排序链表中的重复元素](https://juejin.cn/post/7060364462942846990/)

[82. 删除排序链表中的重复元素 II](https://juejin.cn/post/7060532039564394504/)

2022.02.02

[K 个一组翻转链表](https://juejin.cn/post/7059967145345548318/)

[61.旋转链表](https://juejin.cn/post/7060025838988689445/)

[24. 两两交换链表中的节点](https://juejin.cn/post/7060162016211632158/)

2022.01.30

[反转链表-掘金](https://juejin.cn/post/7058813856398704654/)

[反转链表II-掘金](https://juejin.cn/post/7058830306307997704/)

2022.01.29

[环形链表II-掘金](https://juejin.cn/post/7058548911794814984)

[快乐数](https://juejin.cn/user/624953351216014)

2022.01.28

[环形链表-掘金](https://juejin.cn/post/7058155551993102366)

2021.12.22

leetcode-环形链表II并记录思路

2021.12.21

leetcode-环形链表

2021.12.16

1. 使用mock获取测试数据
2. 了解PM2

2021.12.09

1. 学习Nuxtjs
2. 创建了Nuxtjs项目

2021.12.08
1. 了解服务端渲染和预渲染区别
2. 了解Nuxtjs

2021.12.02
1. 选择排序
2. 快速排序

2021.12.01
1. 插入排序
2. 希尔排序
