---
layout:         "post"
title:          "剑指offer-10-I.斐波那契数列"
subtitle:       "斐波那契数列"
description:    "写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）"
date:           "2022-11-14T23:14:22+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-10-I-fei-bo-na-qi-shu-lie-lcof"
image:          ""
tags:
  - LeetCode
  - 剑指offer
  - 动态规划
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/)

写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。斐波那契数列的定义如下：

```shell
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), 其中 N > 1.
```

斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

- 示例1:
  - 输入：\
    n = 2
  - 输出：\
    1

- 示例2:
  - 输入：\
    n = 5
  - 输出：\
    5

- 提示：
  - 0 <= n <= 100

## 解题思路

### 动态规划

1. 设 `dp` 为一维数组，其中 `dp[i]` 的值代表 斐波那契数列第 `i` 个数字 。
2. `dp[i+1]=dp[i]+dp[i−1]` ，即对应数列定义 `f(n+1)=f(n)+f(n−1)`
3. `dp[0]=0, dp[1]=1` ，即初始化前两个数字；
4. `dp[n]` ，即斐波那契数列的第 `n` 个数字

## 代码解法

### Java

```java
class Solution {
    public int fib(int n) {
        int a = 0, b = 1, sum;
        for(int i = 0; i < n; i++){
            sum = (a + b) % 1000000007;
            a = b;
            b = sum;
        }
        return a;
    }
}
```

### Python

```python
class Solution:
    def fib(self, n: int) -> int:
        a, b = 0, 1
        for _ in range(n):
            a, b = b, a + b
        return a % 1000000007

```
