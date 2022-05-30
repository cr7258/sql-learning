思路：
- 1.从 RequestAccepted 表中获得通过请求数，从 FriendRequest 表中获得请求总数，相除得到结果。
- 2.ROUND 函数取 2 位小数。
- 3.当 FriendRequest 表为空时，总请求数，也就是分母，有可能为 0。所以我们需要使用 ifnull 函数来处理这种特殊情况。


```sql
SELECT 
    ROUND(
        IFNULL (
            (SELECT COUNT(*) FROM (SELECT DISTINCT requester_id, accepter_id FROM RequestAccepted) AS A)
            /
            (SELECT COUNT(*) FROM (SELECT DISTINCT sender_id, send_to_id FROM FriendRequest) AS B),
            0)
        , 2) AS accept_rate;
```