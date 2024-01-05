Input:
Customer table:
+-------------+-------------+
| customer_id | product_key |
+-------------+-------------+
| 1 | 5 |
| 2 | 6 |
| 3 | 5 |
| 3 | 6 |
| 1 | 6 |
+-------------+-------------+
Product table:
+-------------+
| product_key |
+-------------+
| 5 |
| 6 |
+-------------+
Output:
+-------------+
| customer_id |
+-------------+
| 1 |
| 3 |
+-------------+
Explanation:
The customers who bought all the products (5 and 6) are customers with IDs 1 and 3.

```sql
SELECT  customer_id
FROM Customer
GROUP BY customer_id
HAVING COUNT(distinct product_key) = (SELECT COUNT(product_key) FROM Product)
```

SELECT customer_id: Đây là phần chính của câu truy vấn, cho biết chúng ta muốn chọn cột "customer_id" từ bảng "Customer".

FROM Customer: Xác định bảng nguồn từ đó dữ liệu sẽ được chọn, trong trường hợp này là bảng "Customer".

GROUP BY customer_id: Nhóm dữ liệu theo các ID khách hàng duy nhất. Điều này cần thiết để thực hiện các hàm tổng hợp trên từng nhóm.

HAVING COUNT(distinct product_key) = (SELECT COUNT(product_key) FROM Product): Điều này là điều kiện để lọc kết quả. Nó sử dụng mệnh đề HAVING, tương tự như mệnh đề WHERE nhưng được sử dụng với các hàm tổng hợp. Điều kiện kiểm tra xem số lượng product_key duy nhất cho mỗi khách hàng có bằng với tổng số product_key trong bảng "Product" hay không.

COUNT(distinct product_key): Đếm số lượng product_key duy nhất mà mỗi khách hàng đã mua.
(SELECT COUNT(product_key) FROM Product): Subquery tính tổng số product_key trong bảng "Product".
Nếu số lượng product_key duy nhất cho một khách hàng khớp với tổng số product_key, có nghĩa là khách hàng đó đã mua tất cả các sản phẩm. Do đó, customer_id sẽ được bao gồm trong bộ kết quả cuối cùng.
