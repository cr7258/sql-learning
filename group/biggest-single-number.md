思路：
1.根据 num 进行分组，过滤出单一数字。
2.使用 MAX() 函数求出最大 num 。
```sql
SELECT MAX(num) AS num FROM (
    SELECT num FROM MyNumbers
    GROUP BY num 
    HAVING COUNT(num) = 1
) t
```