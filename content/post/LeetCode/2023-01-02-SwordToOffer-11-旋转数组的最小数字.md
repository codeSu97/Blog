---
layout:         "post"
title:          "剑指offer-11-旋转数组的最小数字"
subtitle:       "旋转数组的最小数字"
description:    "把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转"
date:           "2023-01-12T21:58:13+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-11-xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof"
image:          ""
draft:          true
tags:
  - LeetCode
  - 剑指offer
  - 算法
  - 数组
  - 二分查找
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode.cn/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/?favorite=xb9nqhhg)

把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。
给你一个可能存在 重复 元素值的数组 numbers ，它原来是一个升序排列的数组，并按上述情形进行了一次旋转。请返回旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一次旋转，该数组的最小值为 1。  
注意，数组 [a[0], a[1], a[2], ..., a[n-1]] 旋转一次 的结果为数组 [a[n-1], a[0], a[1], a[2], ..., a[n-2]] 。

- 示例1:
  - 输入：\
    numbers = [3,4,5,1,2]
  - 输出: \
    1

- 示例2:
  - 输入：\
    numbers = [2,2,2,0,1]
  - 输出: \
    0

- 限制：
  - n == numbers.length
  - 1 <= n <= 5000
  - -5000 <= numbers[i] <= 5000
  - numbers 原来是一个升序排序的数组，并进行了 1 至 n 次旋转

## 解题思路

### 二分法

1. 初始化双指针，`start=0，end=len-1`
2. 循环二分，找到中点，`medium = (start + end) // 2`
    1. 当 `nums[medium] > nums[end]`，最小元素在数组右侧，即`start = medium+1`
    2. 当 `nums[medium] < nums[end]`，最小元素在数组左侧，即`end = medium`
    3. 当 `nums[medium] == nums[end]`，无法确定最小元素位置，缩小范围，`end = end - 1`
3. 循环结束，返回`nums[start]`

## 代码解法

### Python

```python
from typing import List


class Solution:
    def minArray(self, numbers: List[int]) -> int:
        start, end = 0, len(numbers) - 1
        while start < end:
            medium = (start + end) // 2
            if numbers[medium] > numbers[end]:
                start = medium + 1
            elif numbers[medium] < numbers[end]:
                end = medium
            else:
                end -= 1
        return numbers[start]

```
