```sql
SELECT e.employee_id, b.team_size FROM Employee e
LEFT JOIN (
    SELECT team_id, COUNT(*) AS team_size FROM Employee
    GROUP BY team_id
) b
ON e.team_id= b.team_id
```