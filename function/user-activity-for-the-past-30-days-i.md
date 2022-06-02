思路：
- 1.筛选出 activity_date 0 ~ 29 天的数据
- 2.根据 activity_date 分组，然后计算去重后的 user_id 数量
```sql
SELECT activity_date AS day, COUNT(DISTINCT user_id) AS active_users FROM Activity
WHERE DATEDIFF('2019-07-27', activity_date) BETWEEN 0 AND 29
GROUP BY activity_date
```