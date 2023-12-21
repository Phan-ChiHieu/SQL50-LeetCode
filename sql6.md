Table: Employees

+---------------+---------+
| Column Name | Type |
+---------------+---------+
| id | int |
| name | varchar |
+---------------+---------+
id is the primary key (column with unique values) for this table.
Each row of this table contains the id and the name of an employee in a company.

Table: EmployeeUNI

+---------------+---------+
| Column Name | Type |
+---------------+---------+
| id | int |
| unique_id | int |
+---------------+---------+
(id, unique_id) is the primary key (combination of columns with unique values) for this table.
Each row of this table contains the id and the corresponding unique id of an employee in the company.

Viết giải pháp hiển thị ID duy nhất của mỗi người dùng. Nếu người dùng không có ID duy nhất, hãy thay thế chỉ hiển thị null.

```sql
SELECT name, unique_id
FROM Employees e
LEFT JOIN EmployeeUNI eu ON e.id = eu.id;
```

    - LEFT JOIN là một trong những loại join trong SQL, nó được sử dụng để kết hợp các hàng từ bảng bên trái (từ bảng xuất hiện trước trong câu lệnh SQL) với các hàng từ bảng bên phải (từ bảng xuất hiện sau trong câu lệnh SQL) dựa trên một điều kiện kết hợp. Nếu không có sự khớp hợp nào, các cột từ bảng bên phải sẽ chứa giá trị NULL.
