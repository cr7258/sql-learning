
思路：
1.一列一列处理：把“列名”做为新列的 value（如本题的 store），把原来的 value 也作为新列（如本题的 price）。
2.用 UNION ALL 拼接每一列的结果。
3.注意本题如果这一产品在商店里没有出售，则不输出这一行，所以要原列  is not NULL 的筛选条件。

```sql
SELECT product_id, 'store1' AS store, store1 AS price
FROM Products WHERE store1 is not NULL
UNION ALL
SELECT product_id, 'store2' AS store, store2 AS price
FROM Products WHERE store2 is not NULL
UNION ALL
SELECT product_id, 'store3' AS store, store3 AS price
FROM Products WHERE store3 is not NULL
```