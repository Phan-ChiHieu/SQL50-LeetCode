Table: Cinema

+----------------+----------+
| Column Name | Type |
+----------------+----------+
| id | int |
| movie | varchar |
| description | varchar |
| rating | float |
+----------------+----------+
id is the primary key (column with unique values) for this table.
Each row contains information about the name of a movie, its genre, and its rating.
rating is a 2 decimal places float in the range [0, 10]

Write a solution to report the movies with an odd-numbered ID and a description that is not "boring".

Example 1:

Input:
Cinema table:
+----+------------+-------------+--------+
| id | movie | description | rating |
+----+------------+-------------+--------+
| 1 | War | great 3D | 8.9 |
| 2 | Science | fiction | 8.5 |
| 3 | irish | boring | 6.2 |
| 4 | Ice song | Fantacy | 8.6 |
| 5 | House card | Interesting | 9.1 |
+----+------------+-------------+--------+
Output:
+----+------------+-------------+--------+
| id | movie | description | rating |
+----+------------+-------------+--------+
| 5 | House card | Interesting | 9.1 |
| 1 | War | great 3D | 8.9 |
+----+------------+-------------+--------+
Explanation:
We have three movies with odd-numbered IDs: 1, 3, and 5. The movie with ID = 3 is boring so we do not include it in the answer.

```sql
SELECT * FROM Cinema
WHERE MOD(id,2) = 1 AND description <> 'boring'
ORDER BY rating DESC
```

- SELECT \* FROM Cinema: Chọn tất cả các cột từ bảng "Cinema".

- WHERE MOD(id, 2) = 1: Lựa chọn các dòng trong đó giá trị của cột "id" khi chia cho 2 dư 1. Điều này đồng nghĩa với việc chỉ chọn các bản ghi có giá trị id là số lẻ.

- AND description <> 'boring': Tiếp theo, chỉ chọn các dòng trong đó giá trị của cột "description" không phải là 'boring'. Điều này loại bỏ các bản ghi có mô tả là 'boring'.

- ORDER BY rating DESC: Sắp xếp kết quả theo cột "rating" theo thứ tự giảm dần (DESC).
