title: LeetCode 4 - Median of Two Sorted Arrays 两个有序数组的中位数
Slug: 
Date: 2018-03-07 22:50
Category: posts
Tags: LeetCode
Author: Binboy
Summary: Read it to find out.

# LeetCode 4 - Median of Two Sorted Arrays
## 两个有序数组的中位数

### 题目描述

> There are two sorted arrays nums1 and nums2 of size m and n respectively.
> Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

有两个有序数组`nums1`和`nums2`, 长度分别为`m`、`n`。找出这两个有序数组合并后的中位数。复杂度不超过 `O(log(m+n)`

#### 测试用例

```
// 若合并后的长度为奇数
nums1 = [1, 3]
nums2 = [2]

The median is 2.0

// 若合并后的长度为偶数
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

