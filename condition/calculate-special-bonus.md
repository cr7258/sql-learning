
思路：
方法一：使用 IF 判断。

```sql
SELECT 
    employee_id, 
    IF (employee_id % 2 = 1 and left(name, 1) != 'M', salary, 0) as bonus
FROM Employees; 
```
方法二：使用 CASE WHEN。
```sql
SELECT 
    employee_id,
    CASE
    WHEN employee_id % 2 = 1 and left(name, 1) != 'M' THEN 
        salary
    ELSE 
        0
    END AS bonus
FROM Employees;
```

求余可以使用 MOD 函数，正则匹配可以使用 RLIKE。
```sql
SELECT
    employee_id, 
CASE WHEN 
    MOD(employee_id, 2) = 1 AND name NOT RLIKE '^M' THEN salary ELSE 0 END AS bonus 
FROM
	Employees 
ORDER BY 
    employee_id;
```