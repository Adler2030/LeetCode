# [344 反转字符串](https://leetcode.cn/problems/reverse-string/)

### 解题思路

双指针,进行原地替换

### 代码实现

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        left, right = 0, len(s) - 1

        while left <= right:
            s[left], s[right] = s[right], s[left]
            left += 1
            right -= 1

```

