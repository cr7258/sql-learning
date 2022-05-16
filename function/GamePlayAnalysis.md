思路：使用 MIN 函数获取日期的最小值。
```sql
SELECT player_id, MIN(event_date) AS first_login FROM Activity
GROUP BY player_id
```

