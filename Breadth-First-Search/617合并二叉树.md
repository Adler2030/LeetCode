# [617 合并二叉树](https://leetcode.cn/problems/merge-two-binary-trees/https://leetcode.cn/problems/merge-two-binary-trees/)

### 解题思路

对root1,root2进行广度优先搜索,并在root1上修改

1. 假若p,q两个结点都存在,则对p的值进行+=操作
2. 当p,q左子结点都存在时,添加到队列中,假若只有q左子结点存在,则对p左子结点赋值
3. 右子结点同理

### 代码实现

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def mergeTrees(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root1:
            return root2
        if not root2:
            return root1

        queue = collections.deque([(root1, root2)])

        while queue:
            p, q = queue.popleft()
            if p and q:
                p.val += q.val
            
            if p.left and q.left:
                queue.append((p.left, q.left))
            elif q.left:
                p.left = q.left 
            
            if p.right and q.right:
                queue.append((p.right, q.right))
            elif q.right:
                p.right = q.right 
        
        return root1

```

