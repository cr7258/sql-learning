思路：
1.使用 CASE WHEN 语句进行条件判断，如果是买入，价格为负数。
```sql
SELECT stock_name, SUM(
    CASE WHEN operation = 'Buy'
    THEN -price
    ELSE price
    END 
) AS capital_gain_loss
FROM Stocks
GROUP BY stock_name
ORDER BY operation_day
```