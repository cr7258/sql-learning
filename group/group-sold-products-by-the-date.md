思路：GROUP_CONCAT 函数组内拼接，根据 sell_date 分组。

```sql
select
    sell_date,
    count(distinct product) num_sold,
    GROUP_CONCAT(distinct product) products
from
    activities
group by sell_date
order by sell_date;

```