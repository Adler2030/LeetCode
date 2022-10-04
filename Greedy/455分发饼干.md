# [455 分发饼干](https://leetcode.cn/problems/assign-cookies/)

### 解题思路

将数组排序后，从大到小寻找满足的情况

### 代码实现

```python
class Solution:
    def findContentChildren(self, g: List[int], s: List[int]) -> int:
        g.sort(reverse=True)
        s.sort(reverse=True)

        i = j = result = 0
        while i < len(g) and j < len(s):
            if g[i] <= s[j]:
                j += 1
                result += 1
            i += 1

        return result
```

