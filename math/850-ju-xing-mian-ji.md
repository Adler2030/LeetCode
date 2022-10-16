# 850 矩形面积

### 解题思路

**扫描线**

可以运用扫描线的方法实现，下图为y轴扫描，本题x轴扫描

![scanning.svg](https://pic.leetcode-cn.com/1663294002-IWgpYx-scanning.svg)

1. 首先将每个举行的分界线的x坐标添加到集合中，然后使用pairwise成对遍历start，end，x方向长度即为end-start，x方向的长度不是问题，难点在于y方向的高度
2. 假设start, end是两个相邻的分界线的x坐标，我们可以获取该区间边界外的矩形的下边界y0，上边界y1，然后按y0正序排序
3. 用cur记录上次的最大y坐标，与下次进行比较，分有交集（在不满足cur < y0下cur < y1）或者无交集（cur < y0）两种情况进行计算

### 代码实现

```python
class Solution:
    def rectangleArea(self, rectangles: List[List[int]]) -> int:
        x_set = set()
        ans = 0
        for rectangle in rectangles:
            x_set.add(rectangle[0])
            x_set.add(rectangle[2])
        
        x_set = sorted(x_set)
        # 纵向x轴扫描线
        for start, end in pairwise(x_set):
            y_list = [(y1, y2) for x1, y1, x2, y2 in rectangles if x1 <= start and x2 >= end]

            s = cur = 0
            # 横向y轴扫描线
            for y0, y1 in sorted(y_list, key=lambda x: x[0]):
                if y0 > cur:  # cur < y0, 说明与前一个矩形在区间[start, end]无交集, 高度加y1 - y0
                    s += y1 - y0
                elif y1 > cur:  # 在不满足cur < y0下cur < y1, 说明有交集,高度加y1-cur
                    s += y1 - cur
                cur = max(cur, y1)  # 使用cur来记录上一次的y1，作比较
            ans += s * (end - start)

        return ans % 1000000007

```
