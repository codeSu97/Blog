---
layout:         "post"
title:          "剑指offer-09.用两个栈实现队列"
subtitle:       "用两个栈实现队列"
description:    "用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能"
date:           "2022-11-14T21:25:18+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-09-yong-liang-ge-zhan-shi-xian-dui-lie-lcof"
image:          ""
tags:
  - LeetCode
  - 剑指offer
  - 栈
  - 设计
  - 队列
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。

(若队列中没有元素，deleteHead 操作返回 -1 )

- 示例1:
  - 输入：\
    ["CQueue","appendTail","deleteHead","deleteHead"]\
    [[],[3],[],[]]
  - 输出：\
    [null,null,3,-1]

- 示例2:
  - 输入：\
    ["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]\
    [[],[],[5],[2],[],[]]
  - 输出：\
    [null,-1,null,null,5,2]

- 提示：
  - 1 <= values <= 10000
  - 最多会对 appendTail、deleteHead 进行 10000 次调用

## 解题思路

1. 栈先进后出，无法实现队列功能
2. 双栈实现队列，定义两个栈
   1. 一个栈`inStack`实现入队，一个栈`outStack`实现出队
   2. 循环把`inStack`的元素出栈到`outStack`中，实现`inStack`的倒序
   3. `outStack`的出栈即为队列的出队
3. appendTail() 函数，直接把value添加到 `inStack`中
4. deleteTail() 函数，有三种情况
   1. 当`outStack`不为空，`outStack`中还有已完成倒序的元素，即没有全部出队，出队操作即为`outStack`的出栈
   2. 当`inStack`为空，即两个栈都为空，则返回 `-1`
   3. 否则，将`inStack`全部倒序到`outStack`中，并返回`outStack`的栈顶

## 代码解法

### Java

```java
import java.util.LinkedList;

class CQueue {

    LinkedList<Integer> inStack, outStack;

    public CQueue() {
        inStack = new LinkedList<>();
        outStack = new LinkedList<>();
    }

    public void appendTail(int value) {
        inStack.add(value);
    }

    public int deleteHead() {
        if (!outStack.isEmpty()) {
            return outStack.removeLast();
        } else if (inStack.isEmpty()) {
            return -1;
        }

        while (!inStack.isEmpty()) {
            outStack.addLast(inStack.removeLast());
        }

        return outStack.removeLast();
    }
}

/**
 * Your CQueue object will be instantiated and called as such:
 * CQueue obj = new CQueue();
 * obj.appendTail(value);
 * int param_2 = obj.deleteHead();
 */
```

### Python

```python
class CQueue:
    def __init__(self):
        self.in_stack = []
        self.out_stack = []

    def appendTail(self, value: int) -> None:
        self.in_stack.append(value)

    def deleteHead(self) -> int:
        if self.out_stack:
            return self.out_stack.pop()
        if not self.in_stack:
            return -1
        while self.in_stack:
            self.out_stack.append(self.in_stack.pop())
        return self.out_stack.pop()
```
