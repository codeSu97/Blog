---
layout:         "post"
title:          "剑指offer-10-II.青蛙跳台阶问题"
subtitle:       "青蛙跳台阶问题"
description:    "一直青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个n级台阶总共有多少种跳法"
date:           "2023-01-02T16:26:45+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-10-II-qing-wa-tiao-tai-jie-wen-ti-lcof"
image:          ""
draft:          true
tags:
  - LeetCode
  - 剑指offer
  - 动态规划
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode.cn/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/?favorite=xb9nqhhg)

一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

- 示例1:
  - 输入：\
    n = 2
  - 输出：\
    2

- 示例2:
  - 输入：\
    n = 7
  - 输出：\
    21

- 示例3:
  - 输入：\
    n = 0
  - 输出：\
    1

- 提示：
  - 0 <= n <= 100

## 解题思路

### 动态规划

1. 跳上n级台阶有f(n)种跳法，
