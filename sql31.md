In SQL, (x, y, z) is the primary key column for this table.
Each row of this table contains the lengths of three line segments.


Example 1:

Input:
Triangle table:
+----+----+----+
| x | y | z |
+----+----+----+
| 13 | 15 | 30 |
| 10 | 20 | 15 |
+----+----+----+
Output:
+----+----+----+----------+
| x | y | z | triangle |
+----+----+----+----------+
| 13 | 15 | 30 | No |
| 10 | 20 | 15 | Yes |
+----+----+----+----------+

```sql
select x, y, z,
case when x + y > z and x + z > y and y + z > x then 'Yes'
     else 'No'
end as triangle
from Triangle
```

```sql
SELECT *, IF(x+y>z and y+z>x and z+x>y, "Yes", "No") as triangle FROM Triangle
```
