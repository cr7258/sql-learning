
思路：
1. 从表 p1 取出 3 条记录；
2. 拿着第 1 条记录去表 p2 查找满足 WHERE 的记录，代入该条件 p1.Email = p2.Email AND p1.Id > p2.Id 后，发现没有满足的，所以不用删掉记录 1；
3. 记录 2 同理；
4. 拿着第 3 条记录去表 p2 查找满足 WHERE 的记录，发现有一条记录满足，所以要从 p1 删掉记录 3；
5. 3 条记录遍历完，删掉了 1 条记录，这个 DELETE 也就结束了。
```sql
DELETE p1 FROM Person p1,
    Person p2
WHERE
    p1.Email = p2.Email AND p1.Id > p2.Id
```