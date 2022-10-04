# [103 二叉树的锯齿形层序遍历](https://leetcode.cn/problems/binary-tree-zigzag-level-order-traversal/)

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
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []

        queue = collections.deque()
        check = 0
        queue.append(root)
        result = []
        while queue:
            tmp = []
            n = len(queue)
            for i in range(n):
                node = queue.popleft()
                if node:
                    tmp.append(node.val)

                    queue.append(node.left)
                    queue.append(node.right)

            if tmp:
                result.append(tmp[::-1]) if check else result.append(tmp)

            check = 0 if check else 1

        return result

```

