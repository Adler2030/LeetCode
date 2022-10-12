# [283 移动零](https://leetcode.cn/problems/move-zeroes/)

### 解题思路

定义指针j指向值为0的元素,另一个指针由for循环产生

### 代码实现

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        j = 0  # 指向值为0的元素

        for i in range(n):
            if nums[i]:
                nums[i], nums[j] = nums[j], nums[i]
                j += 1

```

