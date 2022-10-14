# [733 图像渲染](https://leetcode.cn/problems/flood-fill/)

### 解题思路

> 广度优先搜索

从起点开始,向四个方向扩散,扩散过程中限制坐标,用队列存储坐标元组(nx, ny)

### 代码实现

```py
class Solution:
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
        init_color = image[sr][sc]
        if init_color == color:
            return image

        n, m = len(image), len(image[0])
        image[sr][sc] = color
        queue = collections.deque([(sr, sc)])

        while queue:
            x, y = queue.popleft()

            for i, j in [(0, 1), (1, 0), (0, -1), (-1, 0)]:
                nx = x + i
                ny = y + j
                if 0 <= nx < n and 0 <= ny <m and image[nx][ny] == init_color:
                    queue.append((nx, ny))
                    image[nx][ny] = color
        
        return image
```

