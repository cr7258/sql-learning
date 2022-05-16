思路：根据 visit_id 进行两表关联，查询没有交易的顾客，然后根据顾客进行分组，最后通过计算 count 得到顾客只光顾不交易的次数。
```sql
SELECT 
    customer_id, count(customer_id) count_no_trans
FROM 
    Visits v
LEFT JOIN
    Transactions t ON t.visit_id = v.visit_id
WHERE amount IS NULL
GROUP BY customer_id
```