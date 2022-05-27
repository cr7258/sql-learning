思路：
1.将数组降序（由大到小）排列，在序列的第 N 位（即下标为 N-1）开始，取 1 个元素，即该元素为第 N 位大。
2.因为 LIMIT 的起始索引是实际位置减 1 所以我们先把 N-1。
```sql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
    SET N = N-1;
  RETURN (
      SELECT salary FROM employee
      GROUP BY salary
      ORDER BY salary DESC
      LIMIT N,1
  );
END
```