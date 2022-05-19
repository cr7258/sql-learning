思路：使用 ON 在查询时进行过滤 a.managerId = b.id AND a.salary > b.salary。

```sql
SELECT a.Name AS Employee FROM Employee AS a
INNER JOIN Employee AS b 
ON a.managerId = b.id AND a.salary > b.salary
```