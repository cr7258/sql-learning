
```sql
SELECT DISTINCT a.seat_id
FROM cinema a JOIN cinema b
ON ABS(a.seat_id - b.seat_id) = 1 AND a.free = 1 AND b.free = 1
ORDER BY a.seat_id
```

参考资料：
- [连续空余座位](https://leetcode.cn/problems/consecutive-available-seats/solution/lian-xu-kong-yu-zuo-wei-by-leetcode/)