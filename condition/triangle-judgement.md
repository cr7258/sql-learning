思路：三角形任意两边之和大于第三边，任意两边之差小于第三边。
```sql
SELECT x, y, z, 
    CASE
        WHEN x + y > z AND x + z > y AND z + y > x THEN 'Yes'
        ELSE 'No'
    END AS 'triangle'
FROM triangle
```