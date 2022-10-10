# [977 有序数组的平方](https://leetcode.cn/problems/squares-of-a-sorted-array/)

### 解题思路

双指针

### 代码实现

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        left, right, pos = 0, len(nums) - 1, len(nums) - 1
        result = [0] * len(nums)
        while left <= right:
            if abs(nums[left]) > abs(nums[right]):
                result[pos] = nums[left] ** 2
                left += 1
            else:
                result[pos] = nums[right] ** 2
                right -= 1
            pos -= 1

        return result
```

