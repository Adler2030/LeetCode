# Template

1. 初始化队列
2. 将初始元素添加队列中
3. 遍历队列

```py
# 示例 944
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        queue = collections.deque()
        m, n = len(grid), len(grid[0])
        time = 0

        for i in range(m):
            for j in range(n):
                if grid[i][j] == 2:
                    queue.append((i, j, time))
        
        while queue:
            x, y, time = queue.popleft()
            for i, j in [(0, 1), (1, 0), (0, -1), (-1, 0)]:
                nx = x + i
                ny = y + j
                if 0 <= nx < m and 0 <= ny < n and grid[nx][ny] == 1:
                    grid[nx][ny] = 2
                    queue.append((nx, ny, time + 1))  # 满足条件的位置，需要的时间加1
        
        for row in grid:
            if 1 in row:
                return -1
        
        return time

```

