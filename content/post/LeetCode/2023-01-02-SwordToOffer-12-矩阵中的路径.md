---
layout:         "post"
title:          "剑指offer-12-矩阵中的路径"
subtitle:       "矩阵中的路径"
description:    "给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false"
date:           "2023-01-12T22:58:13+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-12-ju-zhen-zhong-de-lu-jing-lcof"
image:          ""
draft:          true
tags:
  - LeetCode
  - 剑指offer
  - 数组
  - 回溯
  - 矩阵
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode.cn/problems/ju-zhen-zhong-de-lu-jing-lcof/?favorite=xb9nqhhg)

给定一个 m x n 二维字符网格 board 和一个字符串单词 word 。如果 word 存在于网格中，返回 true ；否则，返回 false 。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。

例如，在下面的 3×4 的矩阵中包含单词 "ABCCED"（单词中的字母已标出）。

![3x4矩阵](https://assets.leetcode.com/uploads/2020/11/04/word2.jpg)

- 示例1:
  - 输入：\
    board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
  - 输出: \
    true

- 示例2:
  - 输入：\
    board = [["a","b"],["c","d"]], word = "abcd"
  - 输出: \
    false

- 提示：
  - m == board.length
  - n = board[i].length
  - 1 <= m, n <= 6
  - 1 <= word.length <= 15
  - board 和 word 仅由大小写英文字母组成

## 解题思路
