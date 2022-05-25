思路：首先，我们用一个临时表保存向 RED 公司销售过东西的人，然后利用姓名信息将这个表和 salesperson 表建立联系。
```sql
SELECT s.name
FROM SalesPerson s 
WHERE s.sales_id NOT IN (
SELECT
    o.sales_id
FROM
    orders o
        LEFT JOIN
    company c ON o.com_id = c.com_id
WHERE
    c.name = 'RED'
)
```