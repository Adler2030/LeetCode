# [994 腐烂的橘子](https://leetcode.cn/problems/rotting-oranges/)

### 解题思路

1. 将所有腐烂的橘子坐标加入队列中
2. 遍历队列，遍历弹出元素的四个方向，满足条件的则置2，并将其添加到队列中
3. 使用time变量记录所需的时间，初始为0，随坐标一起进出队列。每次遍历都对time重新赋值，当遍历到最后时，可以确保time为最后一个橘子腐烂所需要的时间

### 代码实现

```python
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

