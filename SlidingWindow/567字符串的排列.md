# [567 字符串的排列](https://leetcode.cn/problems/permutation-in-string/) 

### 解题思路

> 根据题目要求,字符串是乱序的,但是要求必须连续,所以可以统计字符串中各字符的数目进行比较

1. 定义两个字典counter,counter2分别存储s1,滑动数组中的元素及其出现次数
2. left,right记录滑动数组边界
3. counter2在初始化的时候右边界少1,以便能正常开始循环.
4. 判断right所在元素是否在字典中并作不同处理
5. 之后比较两个字典,相同则返回True
6. 不同,则要将最左侧元素数目减1,数目为0则要从字典弹出
7. 最后left/right均加1



### 代码实现

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        counter = collections.Counter(s1)
        n = len(s2)

        left, right = 0, len(s1) - 1

        counter2 = collections.Counter(s2[left:right])

        while right < n:
            if s2[right] in counter2:
                counter2[s2[right]] += 1
            else:
                counter2[s2[right]] = 1
            
            if counter2 == counter:
                return True

            counter2[s2[left]] -= 1

            if counter2[s2[left]] == 0:
                counter2.pop(s2[left])
            
            left += 1
            right += 1

        return False
```

