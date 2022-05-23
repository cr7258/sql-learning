
思路：MySQL 使用 DATEDIFF 来比较两个日期类型的值。因此，我们可以通过将 weather 与自身相结合，并使用 DATEDIFF() 函数。
```sql
SELECT a.id AS id FROM Weather a
JOIN Weather b
ON DATEDIFF(a.recordDate, b.recordDate) = 1 
AND a.Temperature > b.Temperature
```