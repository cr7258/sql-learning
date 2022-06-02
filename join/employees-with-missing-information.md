
思路：
- 1.UNION ALL 联合多表，保留两个表中的记录
- 2.GROUP BY 按照 id 分组
- 3.HAVING 条件筛选
- 4.ORDER BY 升序排序
```sql
SELECT employee_id FROM
(
    SELECT employee_id FROM Employees
    UNION ALL
    SELECT employee_id FROM Salaries
) AS t
GROUP BY employee_id
HAVING count(employee_id) = 1
ORDER BY employee_id

```