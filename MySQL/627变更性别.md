# [627 变更性别](https://leetcode.cn/problems/swap-salary/)

### 解题思路

使用update更新表；使用set配合if条件判断来更改表中的值

### 代码实现

```mysql
update
	Salary
set
	sex = if (sex = "f", "m", "f")
```

