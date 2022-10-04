#  [104 二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/)

### 代码实现

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
import collections


class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0

        queue = collections.deque()
        queue.append(root)
        depth = 0
        while queue:
            n = len(queue)
            tmp = []
            for _ in range(n):
                node = queue.popleft()

                if node:
                    tmp.append(node.val)
                    queue.append(node.left)
                    queue.append(node.right)

            if tmp:
                depth += 1

        return depth

```