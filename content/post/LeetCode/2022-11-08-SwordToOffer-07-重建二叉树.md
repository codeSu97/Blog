---
layout:         "post"
title:          "剑指offer-07.重建二叉树"
subtitle:       "重建二叉树"
description:    "输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点"
date:           "2022-11-08T22:54:02+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-06-zhong-jian-er-cha-shu-lcof"
image:          ""
tags:
  - LeetCode
  - 剑指offer
  - 树
  - 数组
  - 哈希表
  - 分治
  - 二叉树
categories: [
    "LeetCode"
]
---

## 题目内容

[原题](https://leetcode.cn/problems/zhong-jian-er-cha-shu-lcof/)

输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。

假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

- 示例1:
  - ![image](https://assets.leetcode.com/uploads/2021/02/19/tree.jpg)
  - 输入：\
    preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
  - 输出：\
    [3,9,20,null,null,15,7]

- 示例2:
  - 输入：\
    preorder = [-1], inorder = [-1]
  - 输出：\
    [-1]

- 限制：
  - 0 <= 节点个数 <= 5000

## 解题思路

### 分治算法

1. 前序遍历性质： 节点按照 `[ 根节点 | 左子树 | 右子树 ]` 排序。 \
   中序遍历性质： 节点按照 `[ 左子树 | 根节点 | 右子树 ]` 排序。
2. 可以得出：
    1. 前序遍历的首元素 为 树的根节点 `node` 的值。
    2. 在中序遍历中搜索根节点 `node` 的索引 ，可将 中序遍历 划分为 `[ 左子树 | 根节点 | 右子树 ]`
    3. 根据中序遍历中的左（右）子树的节点数量，可将 前序遍历 划分为 `[ 根节点 | 左子树 | 右子树 ]`
    4. 可以得出，根节点，左子树根节点，右子树根节点
3. 递归：
    1. 参数：根节点在前序遍历的索引，子树在中序遍历的左边界`left`，子树在中序遍历的右边界`right`
    2. 终止条件：`left > right` ，表明当前已经越过叶节点，终止递归，返回null
    3. 递归：
        1. 建立根节点 `node` ： 节点值为 `preorder[root]`
        2. 划分左右子树： 查找根节点在中序遍历 `inorder[i]`
        3. 构建左右子树：
        |            | 根节点索引 | 中序遍历左边界 | 中序遍历右边界 |
        | ---------- | -------- | ------------ | ----------- |
        | **左子树**  | `root + 1` | `left`         | `i - 1`     |
        | **右子树** | `i - left + root + 1` | `i + 1`| `right` |

4. 返回: 回溯返回 node ，作为上一层递归中根节点的左 / 右子节点

## 代码解法

### Java

```java
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

class Solution {
    int[] preorder;
    HashMap<Integer, Integer> dict = new HashMap<>();
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        this.preorder = preorder;
        for (int i = 0; i < inorder.length; i++) {
            dict.put(inorder[i], i);
        }

        return recur(0, 0, inorder.length - 1);
    }

    TreeNode recur(int root, int left, int right) {
        if (left > right) {
            return null;
        }
        TreeNode head = new TreeNode(preorder[root]);

        int i = dict.get(preorder[root]);
        head.left = recur(root + 1, left, i - 1);
        head.right = recur(root + i - left + 1, i + 1, right);
        return head;
    }
}
```

### Python

```python
from typing import List


class TreeNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None


class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> TreeNode:

        map = dict()
        for index, value in enumerate(inorder):
            map[value] = index

        def recur(root: int, left: int, right: int) -> TreeNode:
            if left > right:
                return None
            head = TreeNode(preorder[root])
            i = map.get(preorder[root])
            head.left = recur(root + 1, left, i - 1)
            head.right = recur(root + i - left + 1, i + 1, right)
            return head
        return recur(0, 0, len(inorder) - 1)

```
