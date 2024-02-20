# Exercise 1

**Merge Sorted Array**

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.

_The code is: (failed)_
```py
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        while m > 0 and n > 0:
            if nums1[m - 1] < nums2[n - 1]:
                nums1[m + n - 1] = nums2[n - 1]
                n -= 1
            else:
                nums1[m + n -1] = nums1[m - 1]
                m -= 1
        if m == 0:
            nums1 = nums2

```

_The code is: (passed)_
```py
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        for ind in range(0, n):
            nums1[m] = nums2[ind]
            m += 1
        nums1.sort()
```

_A brief version:_
```py
class Solution():
    def merge(self, nums1, m, nums2, n):
    for i in range(n):
        nums1[m + i] = nums2[i] # i also adds 1 each loop, so we can use m adds i directly.
    nums1.sort()
```
