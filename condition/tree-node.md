
思路：使用 CASE WHEN 控制流语句判断
Root: 没有父节点
Inner: 它是某些节点的父节点，且有非空的父节点
Leaf: 除了上述两种情况以外的节点

```sql
SELECT
    id,
    CASE
        WHEN tree.id = (SELECT atree.id FROM tree atree WHERE atree.p_id IS NULL)
          THEN 'Root'
        WHEN tree.id IN (SELECT atree.p_id FROM tree atree)
          THEN 'Inner'
        ELSE 'Leaf'
    END AS Type
FROM
    tree
ORDER BY id
;
```