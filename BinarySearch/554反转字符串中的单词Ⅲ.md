# [557 反转字符串中的单词Ⅲ](https://leetcode.cn/problems/reverse-words-in-a-string-iii/?envType=study-plan&id=suan-fa-ru-men&plan=algorithms&plan_progress=sbz3yss)

### 解题思路

双指针或者将字符串分割成单词列表 然后把每个单词反转切片

### 代码实现

```python
# 方法一:双指针
class Solution:
    def reverseWords(self, s: str) -> str:
        s += " "
        result = ""

        i = 0
        for j in range(len(s)):
            if s[j] == " ":
                result += " " + s[i:j][::-1]

                i = j + 1
        
        return result[1:]

# 方法二:对分割后的每个单词倒序排列
class Solution:
    def reverseWords(self, s: str) -> str:
        return ' '.join([letter[::-1] for letter in s.split()])
```

