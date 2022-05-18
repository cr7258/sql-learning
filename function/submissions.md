
思路：
- 1.使用 LEFT 函数获取 name 字段的第一个字符，使用 UPPER 函数转换成大写。
- 2.使用 SUBSTRING 函数截取 name 字段第 2 个字符往后的内容，然后使用 LOWER 函数转换为小写。
- 3.使用 CONCAT 函数拼接。

```sql
SELECT 
   user_id, 
   CONCAT(UPPER(LEFT(name,1)), LOWER(SUBSTRING(name, 2))) name
FROM Users
ORDER BY user_id
```