思路：
- 1、先查询每一个项目中的最大 experience_years。
- 2、再查询每个项目中员工 experience_years = 该项目最大 experience_years 的员工。
```sql
SELECT
	p.project_id,
	p.employee_id
FROM
	Project p
	INNER JOIN Employee e
		ON p.employee_id = e.employee_id
WHERE (p.project_id, e.experience_years) IN (
	SELECT
		p.project_id,
		MAX(e.experience_years)
	FROM
		Project p
		INNER JOIN Employee e
			ON p.employee_id = e.employee_id
	GROUP BY p.project_id
);
```