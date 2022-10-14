# [695 岛屿的最大面积]()

### 解题思路

1. 受733启发, 遍历矩阵中的每个坐标, 当坐标不越界且未触及时进行一次广度优先搜索

2. 在广度优先搜索过程中,注意将遍历过的坐标对应的值置零,并添加到trace中

### 代码实现

```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        def get_area(x, y):
            area = 1
            queue = collections.deque([(x, y)])
            while queue:
                a, b = queue.popleft()
                grid[a][b] = 0
                trace.add((a, b))
                for i, j in [(0, 1), (1, 0), (0, -1), (-1, 0)]:
                    na = a + i
                    nb = b + j
                    if 0 <= na < m and 0 <= nb < n and grid[na][nb] == 1:
                        queue.append((na, nb))
                        grid[na][nb] = 0
                        area += 1

                        trace.add((na, nb))

            return area
            

        trace = set()
        result = 0
        m, n = len(grid), len(grid[0])

        for i in range(m):
            for j in range(n):
                if grid[i][j] != 0 and grid[i][j] not in trace:
                    result = max(result, get_area(i, j))
        
        return result
```

