Title: LeetCode 4 - Median of Two Sorted Arrays
Slug: 分治求解两个有序数组的中位数
Date: 2018-03-07 22:50
Category: posts
Tags: LeetCode
Author: Binboy
Summary: Read it to find out.

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

#### 简单粗暴的思路1

遍历两个数组，在其中找出第k大的元素，时间复杂度`O(m+n)`, 可以实现查找中位数的目的，但不符合题目要求。
简单描述这个思路的实现方式：用两个变量分别指向两个数组，每次取较小值，并向后移动。需要注意的就是奇偶判断，如果是奇数，中位数为`nums[mid]`，如果是偶数，中位数则是`(nums[mid] + nums[mid - 1])/2`.

#### 思路2：分而治之（Divide & Conquer）

> 通过在有序数组中找到一个枢值，将其分为左右两部分，通过对枢值的判断，可将左右某部分忽略，继而在剩下的部分继续寻找新的枢值，直到条件终止。

```swift
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
        let length = nums1.count + nums2.count
        if length % 2 != 0 {
            return findKth(nums1: nums1, nums2: nums2, k: length / 2 + 1)
        } else {
            return (findKth(nums1: nums1, nums2: nums2, k: length / 2) + findKth(nums1: nums1, nums2: nums2, k: length / 2 + 1)) / 2.0
        }
    }
    
    func findKth(nums1: [Int], nums2: [Int], k: Int) -> Double {
        let m = nums1.count
        let n = nums2.count
        // 保证数组1元素更少
        guard m <= n else {
            return findKth(nums1: nums2, nums2: nums1, k: k)
        }
        // 若数组1元素为0，则直接返回数组2中第K个元素
        if m == 0 {
            return Double(nums2[k - 1])
        }
        // 若查找的是第一个元素，则直接比较两个数组的第一个元素，取最小值
        if k == 1 {
            return Double(min(nums1[0], nums2[0]))
        }
        // 开始二分法递归查找
        let i = min(k / 2, m)
        let j = min(k / 2, n)
        
        if nums1[i - 1] < nums2[j - 1] {
            return findKth(nums1: Array(nums1[i..<m]), nums2: nums2, k: k - i)
        } else {
            return findKth(nums1: nums1, nums2: Array(nums2[j..<n]), k: k - j)
        }
    }
}
```

