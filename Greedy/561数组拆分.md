# [561 数组拆分](https://leetcode.cn/problems/array-partition/)

### 解题思路

将数组排序后，步长为2，返回二者最小值以保证整体最大值

### 代码实现

```python
class Solution:
    def arrayPairSum(self, nums: List[int]) -> int:
        nums.sort(reverse=True)

        i = result = 0
        while i < len(nums):
            result += min(nums[i], nums[i + 1])
            i += 2
        
        return result
```

