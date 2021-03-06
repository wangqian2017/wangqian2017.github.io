---
title: LeetCode-006-合并两个有序链表
img: https://miro.medium.com/max/1200/1*9EEAMYxLObepKMaOCgYgvA.jpeg
date: 2020-05-09 20:01:52
tags: [LeetCode]
photos: /medias/featureimages/s29484334.jpg
categories: 数据结构与算法
---

#### 导语
> 本系列为 LeetCode 刷题系列，旨在夯实 JavaScript基础，了解常见算法。 

<!--more-->

# 前言

* 难度：简单

* 设计知识：链表

* 题目地址：https://leetcode-cn.com/problems/merge-two-sorted-lists

* 题目内容：

```
将两个升序链表合并为一个新的升序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

示例：

输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4
```

# 解题

## 解法 - 递归（链表数据结构、边界）

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
var mergeTwoLists = function(l1, l2) {
    // 头结点
    let head = new ListNode()
    // 串联指针
    let cur = head
    while(l1 && l2) {
        // 如果 l2 的结点值较小
        if (l1.val > l2.val) {
            // 先串起 l2 的结点
            cur.next = l2
            // l2 指针向前一步    
            l2 = l2.next
        } else {
            cur.next = l1
            l1 = l1.next
        }
        cur = cur.next
    }
    cur.next = l1 || l2
    return head.next
};
```

* 执行测试

输入：

```
[1,2,4]
[1,3,4]
```

输出：

```
[1,1,2,3,4,4]
```

预期结果：

```
[1,1,2,3,4,4]
```

* 解题思路：

使用递归来解题，将两个链表头部较小的一个与剩下的元素合并，并返回排好序的链表头，当两条链表中的一条为空时终止递归。

* 时间复杂度：O(M+N)

* 空间复杂度：O(M+N)
