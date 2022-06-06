```sql
SELECT c.customer_id, c.customer_name FROM Customers c
LEFT JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id
HAVING
    SUM(IF(product_name='A',1,0))>0 AND
    SUM(IF(product_name='B',1,0))>0 AND
    SUM(IF(product_name='C',1,0))=0
```