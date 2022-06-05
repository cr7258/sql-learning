思路：将表自连接，排除自身，使用 ABS() 函数计算差的绝对值，然后使用 MIN() 函数选出 distance 列中的最小值。
```sql
SELECT MIN(ABS(a.x - b.x)) AS shortest FROM point a
JOIN point b ON a.x != b.x
```