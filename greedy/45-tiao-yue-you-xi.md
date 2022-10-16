# [45 跳跃游戏Ⅱ](https://leetcode.cn/problems/jump-game-ii/)

### 解题思路

定义初始变量

1. end记录当前位置能到达的最远距离
2. part_end记录走一步的最大距离
3. step记录所需的总步数

### 代码实现

```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        end = part_end = step = 0
        for i in range(len(nums) - 1):
            if end >= i:
                end = max(end, i + nums[i])
                if part_end == i:
                    part_end = end
                    step += 1
                
        return step

```

