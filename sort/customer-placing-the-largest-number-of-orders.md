思路：按照订单降序排序后，取第 1 个。
```sql
SELECT customer_number FROM Orders 
GROUP BY customer_number
ORDER BY COUNT(*) DESC LIMIT 1
```