# [21 合并两个有序链表](https://leetcode.cn/problems/merge-two-sorted-lists/)

### 解题思路

- 终止条件：当两个链表都为空时，表示我们对链表已合并完成。
- 调用递归：我们判断 list1和 list2头结点哪个更小，然后较小结点的 next 指针指向其余结点的合并结果。

### 代码实现

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        # 终止条件
        if not list1:
            return list2
        if not list2:
            return list1
        
        # 调用自身
        if list1.val <= list2.val:
            list1.next = self.mergeTwoLists(list1.next, list2)
            return list1
        else:
            list2.next = self.mergeTwoLists(list1, list2.next)
            return list2

```

