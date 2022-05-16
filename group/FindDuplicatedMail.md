
思路：先根据邮箱进行分组，分组后数量大于 1 的就是重复的邮箱。
```sql
SELECT Email FROM Person
GROUP BY Email
Having count(Email) > 1
```

