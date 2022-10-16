# [ 542 01矩阵]()

### 解题思路

> 解题思路类似944,不同点在于多加了一个哈希表,用以记录已经遍历过的坐标

1. 初始化队列
2. 将初始元素0添加队列中
3. 遍历队列,value伴随坐标进出队列,记录数值变化

### 代码实现

```python
class Solution:
    def updateMatrix(self, mat: List[List[int]]) -> List[List[int]]:
        queue = collections.deque()
        m, n = len(mat), len(mat[0])
        value = 0
        seen = set()

        for i in range(m):
            for j in range(n):
                if mat[i][j] == 0:
                    seen.add((i, j))
                    queue.append((i, j, value))

        while queue:
            x, y, value = queue.popleft()
            for i, j in [(0, 1), (1, 0), (0, -1), (-1, 0)]:
                nx = x + i
                ny = y + j
                if 0 <= nx < m and 0 <= ny < n and mat[nx][ny] == 1 and (nx, ny) not in seen:
                    mat[nx][ny] += value
                    seen.add((nx, ny))
                    queue.append((nx, ny, value + 1))
            
        
        return mat
```

