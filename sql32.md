Find all numbers that appear at least three times consecutively.

Input:
Logs table:
+----+-----+
| id | num |
+----+-----+
| 1 | 1 |
| 2 | 1 |
| 3 | 1 |
| 4 | 2 |
| 5 | 1 |
| 6 | 2 |
| 7 | 2 |
+----+-----+
Output:
+-----------------+
| ConsecutiveNums |
+-----------------+
| 1 |
+-----------------+
Explanation: 1 is the only number that appears consecutively for at least three times.

```sql
with cte as (
    select num,
    lead(num,1) over() num1,
    lead(num,2) over() num2
    from logs

)

select distinct num ConsecutiveNums from cte where (num=num1) and (num=num2)
```

Câu lệnh SQL lead(num, 1) over() num1 trong ngữ cảnh của câu truy vấn CTE (Common Table Expression) trong mã bạn đưa ra có thể được giải thích như sau:

lead(num, 1): Đây là sử dụng hàm LEAD() để lấy giá trị của cột num ở hàng kế tiếp (với offset là 1). Nói cách khác, giá trị ở hàng tiếp theo của cột num sẽ được lấy.

over(): Phần này xác định cửa sổ (window) trong đó hàm LEAD() sẽ được áp dụng. Khi không có điều kiện PARTITION BY hoặc ORDER BY được chỉ định, over() sẽ áp dụng hàm trên toàn bộ tập dữ liệu không phân chia cửa sổ và không sắp xếp. Nói một cách đơn giản, nó lấy giá trị của cột num ở hàng kế tiếp trên toàn bộ tập dữ liệu.

num1: Đây là cách đặt tên cho cột kết quả của hàm LEAD(num, 1). Cột này sẽ chứa giá trị của cột num ở hàng kế tiếp.

Vậy nên, cả câu lệnh lead(num,1) over() num1 nói rằng: "Lấy giá trị của cột num ở hàng kế tiếp và đặt nó vào cột có tên là num1". Câu lệnh này được sử dụng trong một CTE để tạo ra tập dữ liệu tạm thời (cte) với các cột num, num1, và num2 để sau đó thực hiện các phân tích và lọc dữ liệu liên quan đến dãy số liên tiếp, như đã giải thích trước đó.

- lead(num, 2) over() num2 nói rằng: "Lấy giá trị của cột num ở hai hàng sau và đặt nó vào cột có tên là num2".
