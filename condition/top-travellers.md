思路 1：IF 条件判断
if (Bool 表达式,为真返回,为假返回)。
```sql
SELECT u.name, IF(SUM(r.distance) IS NULL, 0, SUM(r.distance)) AS travelled_distance FROM Users u
LEFT JOIN Rides r ON u.id = r.user_id 
GROUP BY u.id
ORDER BY travelled_distance DESC, u.name ASC
```

思路 2：COALESCE 函数
格式：COALESCE(表达式 1,表达式 2,...)
按照顺序首先执行表达式 1，如果不为 NULL 则返回表达式 1 的结果
如果为 NULL，则往下执行表达式 2。以此类推。

```sql
SELECT u.name, COALESCE(SUM(r.distance),0) AS travelled_distance FROM Users u
LEFT JOIN Rides r ON u.id = r.user_id 
GROUP BY u.id
ORDER BY travelled_distance DESC, u.name ASC
```