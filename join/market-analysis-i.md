思路：
- 1.使用 Orders 表计算每个用户的产品数。使用 GROUP BY 聚合每个用户的购买记录。使用 YEAR 函数筛选出时间为 2019 年的数据。使用 COUNT(order_id) 计算出每个用户的订单数。
- 2.使用 Users 表得到所有用户及其注册时间。并使用 LEFT JOIN，通过 user_id 和第一步的数据连接，求每个用户的订单数。 如果一个用户没有任何订单，那么第一步的数据中不会有这个用户的数据，最后的 orders_in_2019 会显示为 NULL，所以我们还需要使用 IFNULL，如果数据为 NULL，将其改为 0。
```sql
SELECT u.user_id AS buyer_id, join_date, IFNULL(b.cnt, 0) AS orders_in_2019
FROM Users u
LEFT JOIN (
    SELECT buyer_id, count(order_id) cnt
    FROM Orders
    WHERE YEAR(order_date) = '2019'
    GROUP BY buyer_id
) b
ON u.user_id = b.buyer_id
```