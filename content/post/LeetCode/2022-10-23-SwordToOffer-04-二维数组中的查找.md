---
layout:         "post"
title:          "剑指offer-04.二维数组中的查找"
subtitle:       "查找数组中是否含有该整数"
description:    "在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数"
date:           "2022-10-23T17:59:38+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-04-er-wei-shu-zu-zhong-de-cha-zhao-lcof"
image:          ""
tags:
  - LeetCode
  - 剑指offer
  - 数组
  - 二分查找
  - 分治
  - 矩阵
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode.cn/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)

在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

- 示例:
  现有矩阵 matrix 如下：

  ```Python
    [
        [1,   4,  7, 11, 15],
        [2,   5,  8, 12, 19],
        [3,   6,  9, 16, 22],
        [10, 13, 14, 17, 24],
        [18, 21, 23, 26, 30]
    ]
  ```

  给定 target = 5，返回 true。
  给定 target = 20，返回 false。

- 提示：
  - 0 <= n <= 1000
  - 0 <= m <= 1000

## 解题思路

### 以左上角为原点，旋转45°

1. 以左上角为原点，把矩阵(二维数组)旋转45°
2. 原点的坐标为, `[len(matrix) - 1, 0]`，即`i=len(matrix)-1`, `j=0`
3. 把旋转后的矩阵，看作一棵二叉树，因为该二维数组，从左到右递增，从上到下递增，那么小于根节点的数都在左侧，大于根节点的数都在右侧
4. 遍历数组
    1. `matrix[i][j] < target`，`target`在右侧，即 `j++`
    2. `matrix[i][j] > target`，`target`在左侧，即 `i--`
    3. `matrix[i][j] == target`，返回`True`
5. 遍历完数组，没有返回，说明`target`不在二维数组中，返回`False`

## 代码解法

### Java

```java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        int i = matrix.length - 1, j = 0;

        while (i >= 0 && j < matrix[0].length) {
            if (matrix[i][j] > target) {
                i--;
            } else if (matrix[i][j] < target) {
                j++;
            } else {
                return true;
            }
        }
        return false;
    }
}
```

### Python

```python
from typing import List


class Solution:
    def findNumberIn2DArray(self, matrix: List[List[int]], target: int) -> bool:
        i, j = len(matrix) - 1, 0
        while i >= 0 and j < len(matrix[0]):
            if matrix[i][j] > target:
                i -= 1
            elif matrix[i][j] < target:
                j += 1
            else:
                return True
        return False
```
