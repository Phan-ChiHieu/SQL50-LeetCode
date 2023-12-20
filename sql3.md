Table: World

+-------------+---------+
| Column Name | Type |
+-------------+---------+
| name | varchar |
| continent | varchar |
| area | int |
| population | int |
| gdp | bigint |
+-------------+---------+

name là khóa chính (cột có giá trị duy nhất) cho bảng này.
Mỗi hàng của bảng này cung cấp thông tin về tên của một quốc gia, châu lục mà quốc gia đó thuộc về, diện tích, dân số và giá trị GDP của nó.

Một quốc gia được coi là lớn nếu:

Có diện tích ít nhất ba triệu km2 (tức là 3000000 km2), hoặc
Có dân số ít nhất hai mươi lăm triệu người (tức là 25000000).
Viết một giải pháp để tìm tên, dân số và diện tích của các quốc gia lớn.

```sql
SELECT name, population, area
FROM World
WHERE area >= 3000000 OR population >= 25000000;

```
