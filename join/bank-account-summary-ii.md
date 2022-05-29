```sql
SELECT name,
    SUM(t1.amount) AS balance
FROM  Users AS u1
INNER JOIN Transactions AS t1
ON t1.account = u1.account
GROUP BY u1.account
HAVING SUM(t1.amount) > 10000;
```