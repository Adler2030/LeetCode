# [55 跳跃游戏](https://leetcode.cn/problems/jump-game/)

### 解题思路

遍历nums,判断当前位置是否能到达,并更新能到达的最大距离

### 代码实现

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        end = 0

        for i, num in enumerate(nums):
            if end >= i:
                end = max(i + num, end)
        
        return end >= len(nums) - 1
```

**代码优化**

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        end = 0

        for i, num in enumerate(nums):
            # 之前的max取值可以用i + num > end判断替代
            if end >= i and i + num > end: 
                end = i + num
        
        return end >= len(nums) - 1
```

时间复杂度: O(n)

空间复杂度:O(1)