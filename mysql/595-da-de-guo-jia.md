# [595 大的国家](https://leetcode.cn/problems/big-countries/)

### 解题思路

使用select选择MySQL表所需的行名，from指定表，where后加筛选条件

### 代码实现

```mysql
select
	name, population, area
from
	world
where
	area >= 3000000 or population >= 25000000
```

