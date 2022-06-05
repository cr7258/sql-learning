思路 1：窗口函数（Mysql 8.0 开始支持），格式如下：
```sql
[你要的操作] OVER ( PARTITION BY  <用于分组的列名>
                   ORDER BY <按序叠加的列名> )
```

```sql
SELECT gender, day, 
       SUM(score_points) OVER (PARTITION BY gender ORDER BY day) AS total 
FROM Scores
```

思路 2：根据性别分组的前提下，生成每个日期对应的递归子集，每个子集的和值就是对应日期范围内的累计值。
```sql
SELECT
    t1.gender,
    t1.day,
    SUM(t2.score_points) AS 'total'
FROM
    Scores AS t1
INNER JOIN Scores AS t2 ON t1.day >= t2.day
AND t1.gender = t2.gender
GROUP BY t1.gender, t1.day
ORDER BY t1.gender, t1.day
```