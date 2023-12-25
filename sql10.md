Table: Employee

+-------------+---------+
| Column Name | Type |
+-------------+---------+
| empId | int |
| name | varchar |
| supervisor | int |
| salary | int |
+-------------+---------+
empId is the column with unique values for this table.
Each row of this table indicates the name and the ID of an employee in addition to their salary and the id of their manager.

Table: Bonus

+-------------+------+
| Column Name | Type |
+-------------+------+
| empId | int |
| bonus | int |
+-------------+------+
empId is the column of unique values for this table.
empId is a foreign key (reference column) to empId from the Employee table.
Each row of this table contains the id of an employee and their respective bonus.

```sql
SELECT emp.name, b.bonus
FROM Employee emp
LEFT JOIN  Bonus b ON emp.empId = b.empId
WHERE b.bonus < 1000 OR b.bonus is NULL
```
