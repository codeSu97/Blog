---
layout:         "post"
title:          "剑指offer-03.数组中重复的数字"
subtitle:       "找出数组中重复的数字"
description:    "在一个长度为 n 的数组 `nums` 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字"
date:           "2022-10-23T17:36:51+08:00"
author:         "codeSu"
URL:            "/LeetCode/sword-to-offer-03-shu-zu-zhong-zhong-fu-de-shu-zi-lcof"
image:          ""
tags:
  - LeetCode
  - 剑指offer
  - 数组
  - 哈希表
  - 排序
categories: [
  "LeetCode"
]
---

## 题目内容

找出数组中重复的数字。

在一个长度为 n 的数组 `nums` 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

- 示例1:
  - 输入：\
    [2, 3, 1, 0, 2, 5, 3]
  - 输出：\
    2 或 3

- 限制：
  - 2 <= n <= 100000

## 解题思路

### 哈希表

1. 定义一个哈希表`set`
2. 遍历数组`nums`，每个数字为`num`
   1. 如果`num`在`set`中，说明`num`重复，直接返回`num`
   2. 如果`num`不在`set`中，`set`添加`num`
3. 没有重复的，返回-1

### 原地交换

1. 遍历数组`nums`，依照索引下标
   1. 若 `nums[i] = i` ： 说明此数字已在对应索引位置，无需交换，因此跳过
   2. 若 `nums[nums[i]] = nums[i]` ： 代表索引 `nums[i]` 处和索引 `i` 处的元素值都为 `nums[i]` ，即找到一组重复值，返回此值 `nums[i]`
   3. 否则，交换 索引 `i` 和 `nums[i]` 的值，即 `nums[nums[i]] = nums[i], nums[i] = nums[nums[i]]`
2. 遍历完还没有重复项，则返回 `-1`

## 代码解法

### Java

```java
class Solution {
    public int findRepeatNumber(int[] nums) {
        for (int i = 0; i < nums.length; i++) {
            while(i != nums[i]) {
                if (nums[nums[i]] == nums[i]) {
                    return nums[i];
                }
                int tmp = nums[nums[i]];
                nums[nums[i]] = nums[i];
                nums[i] = tmp;
            }
        }
        return -1;
    }
}
```

### Python

```python
from typing import List


class Solution:
    # 哈希表，判断是否存在
    def findRepeatNumber(self, nums: List[int]) -> int:
        map = set()
        for num in nums:
            if num in map:
                return num
            map.add(num)
        return -1

    # 原地交换
    def findRepeatNumber2(self, nums: List[int]) -> int:
        i = 0
        while i < len(nums):
            if nums[i] == i:
                i += 1
                continue
            if nums[nums[i]] == nums[i]:
                return nums[i]
            nums[nums[i]], nums[i] = nums[i], nums[nums[i]]
        return -1
```
