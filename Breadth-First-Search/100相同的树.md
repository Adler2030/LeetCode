# [100 相同的树](https://leetcode.cn/problems/same-tree/)


### 代码实现

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool """
        if not p and not q:
            return True

        # 用队列保存节点
        queue = [p, q]
        while queue:
            # 从队列中取出两个节点，再比较这两个节点
            left = queue.pop(0)
            right = queue.pop(0)
            # 如果两个节点都为空就继续循环，两者有一个为空就返回false
            if not (left or right):
                continue
            if not (left and right):
                return False
            if left.val != right.val:
                return False
            # 将p的左孩子， q的左孩子放入队列
            queue.append(left.left)
            queue.append(right.left)
            # 将p的右孩子， q的右孩子放入队列
            queue.append(left.right)
            queue.append(right.right)

        return True

```