---
layout:         "post"
title:          "剑指offer-05.替换空格"
subtitle:       "替换字符串中的空格"
description:    "把字符串 s 中的每个空格替换成\"%20\""
date:           "2022-11-02T21:54:28+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-05-ti-huan-kong-ge-lcof"
image:          ""
tags:
  - LeetCode
  - 剑指offer
  - 字符串
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/)

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

- 示例1:
  - 输入：\
    s = "We are happy."
  - 输出：\
    输出："We%20are%20happy."

- 限制：
  - 0 <= s 的长度 <= 10000

## 解题思路

### 遍历

1. Java、Python、go的字符串都是不可变，只能新建一个字符串
2. 初始化一个空数组(Python)/StringBuilder(Java)为res
3. 遍历原字符串，如果字符为空格，转换为%20，否则直接添加至res
4. 把res转换为新的字符串

## 代码解法

### Java

```java
class Solution {
    public String replaceSpace(String s) {
        StringBuilder stringBuildr = new StringBuilder();
        char[] sc = s.toCharArray();
        for (char c : sc) {
            if (' ' == c) {
                stringBuildr.append("%20");
            } else {
                stringBuildr.append(c);
            }
        }
        return stringBuildr.toString();
    }
}
```

### Python

```python
class Solution:
    def replaceSpace(self, s: str) -> str:
        result = []
        for i in s:
            result.append(i) if i != " " else result.append("%20")
        return "".join(result)
```
