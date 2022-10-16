# [112 路径总和](https://leetcode.cn/problems/path-sum/)

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
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False

        queue = collections.deque()
        nums = collections.deque()
        queue.append(root)
        nums.append(targetSum)

        while queue:
            n = len(queue)
            tmp = []
            for _ in range(n):
                node = queue.popleft()

                if node:
                    num = nums.popleft()

                    if not (num - node.val) and not (node.left or node.right):
                        return True

                    if node.left:
                        queue.append(node.left)
                        nums.append(num - node.val)
                    if node.right:
                        queue.append(node.right)
                        nums.append(num - node.val)

        return False

```