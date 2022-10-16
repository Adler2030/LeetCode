# [584 寻找用户推荐人](https://leetcode.cn/problems/find-customer-referee/)

### 解题思路

select–from–where流程

### 代码实现

```mysql
select
	name
from
	customer
where
	referee_id != 2 or referee_id is null
```

