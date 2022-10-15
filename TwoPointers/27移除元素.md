# [27 移除元素](https://leetcode.cn/problems/remove-element/)

### 解题思路

将nums排序后使用双指针将值为val的部分筛选出来

### 代码实现

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        nums.sort()
        left, right = 0, len(nums) - 1

        while left <= right:
            if nums[left] < val:
                left += 1
            elif nums[right] > val:
                right -= 1
            else:
                break
        
        nums[:] = nums[:left] + nums[right + 1:]

        return len(nums)

```

