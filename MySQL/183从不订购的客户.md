# [183 从不订购的客户](https://leetcode.cn/problems/customers-who-never-order/)

### 解题思路

选择Customers中的Name作为Customers，并用not in判断是否订购

### 代码实现

```mysql
select
	Name as Customers
from
	Customers
where
	Id not in (
	select
		CustomerId
	from
		Orders
	)
```

