思路：LEFT JOIN 以左表为基准，如果左表的 personId 不在右表中，则显示为 NULL。
```sql
SELECT FirstName, LastName, City, State FROM Person p
LEFT JOIN Address a
ON p.PersonId = a.PersonId
```