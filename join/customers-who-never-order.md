
思路 1：
- 1.LEFT JOIN 以左表 Customers 为基准，没有订单的客户端的 CustomerId 会为 NULL。
- 2.WHERE o.CustomerId is NULL 会把 CustomerId 为空值的行筛选出来。
```sql
SELECT Name AS Customers
FROM Customers AS c 
LEFT JOIN
Orders AS o
ON c.Id = o.CustomerId
WHERE o.CustomerId is NULL;
```

思路 2：
- 1.嵌套查询，先去 Order 表查询出有订单的 CustomerId。
- 2.从 Customers 表中 NOT IN 排除这些行。
```sql
SELECT Name AS Customers
FROM Customers WHERE Id NOT IN
(
    SELECT CustomerId FROM Orders
)
```

参考资料：
- [图解SQL面试题：查找不在表里的数据](https://leetcode.cn/problems/customers-who-never-order/solution/tu-jie-sqlmian-shi-ti-cha-zhao-bu-zai-biao-li-de-s/)

