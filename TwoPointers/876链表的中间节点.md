# [876 链表的中间节点]()

### 解题思路

方法一:用一个空列表存储遍历的链表,返回中间值

方法二:快慢指针

### 代码实现

```python
# 方法一
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        result = []
        while head:
            result.append(head)
            head = head.next
        
        return result[len(result) // 2]

# 方法二
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        fast = slow = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        
        return slow
    
```

