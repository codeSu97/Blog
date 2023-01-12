---
layout:         "post"
title:          "剑指offer-06.从头到尾打印链表"
subtitle:       "从头到尾打印链表"
description:    "输入一个链表的头节点，从尾到头反过来返回每个节点的值"
date:           "2022-11-02T22:32:08+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-06-cong-wei-dao-tou-da-yin-lian-biao-lcof"
image:          ""
tags:
  - LeetCode
  - 剑指offer
  - 栈
  - 递归
  - 链表
  - 双指针
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)

输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

- 示例1:
  - 输入：\
    head = [1,3,2]
  - 输出：\
    [2,3,1]

- 限制：
  - 0 <= 链表长度 <= 10000

## 解题思路

### 递归

1. 先遍历至链表末端，回溯时依次把节点值加入列表

### 辅助栈

1. 定义两个栈
2. 入栈：遍历整个链表，将各个节点push入栈
3. 出栈：将各个节点值pop出栈，然后依次加入数组

## 代码解法

### Java

```java
class Solution {
    public int[] reversePrint(ListNode head) {
        LinkedList<Integer> stack = new LinkedList<>();
        while (null != head) {
            stack.add(head.val);
            head = head.next;
        }
        int[] res = new int[stack.size()];

        for (int i = 0; i < res.length; i++) {
            res[i] = stack.removeLast();
        }
        return res;
    }
}
```

### Python

```python
# Definition for singly-linked list.
from typing import List


class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None


class Solution:
    # 辅助栈
    def reversePrint(self, head: ListNode) -> List[int]:
        result = []
        while head:
            result.append(head.val)
            head = head.next
        return result[::-1]

    # 递归
    def reversePrint1(self, head: ListNode) -> List[int]:
        return self.reversePrint1(head.next) + [head.val] if head else []

```
