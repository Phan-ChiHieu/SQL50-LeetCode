# Bảng Delivery:

- Bảng này chứa thông tin về việc giao hàng thức ăn cho khách hàng. Các cột bao gồm delivery_id (giá trị duy nhất của bảng), customer_id (mã khách hàng), order_date (ngày đặt hàng), và customer_pref_delivery_date (ngày giao hàng ưu tiên theo yêu cầu của khách hàng).
  Immediate Order và Scheduled Order:

- Nếu ngày giao hàng ưu tiên của khách hàng giống với ngày đặt hàng, thì đơn hàng đó được gọi là "immediate"; ngược lại, nó được gọi là "scheduled".
  First Order của mỗi Khách hàng:

- Đề bài đảm bảo rằng mỗi khách hàng có đúng một đơn đặt hàng đầu tiên. Đơn đặt hàng đầu tiên của mỗi khách hàng là đơn đặt hàng có ngày đặt hàng sớm nhất của họ.
  Yêu cầu cụ thể:

- Bạn cần tính phần trăm đơn hàng ngay lập tức trong số các đơn đặt hàng đầu tiên của tất cả khách hàng.
  Làm tròn kết quả:

- Sau khi tính toán, bạn cần làm tròn phần trăm đến 2 chữ số thập phân.

```sql
Select
    round(avg(order_date = customer_pref_delivery_date)*100, 2) as immediate_percentage
from Delivery
where (customer_id, order_date) in (
  Select customer_id, min(order_date)
  from Delivery
  group by customer_id
);
```

```sql
SELECT
  ROUND((SUM(CASE WHEN order_date = customer_pref_delivery_date THEN 1 ELSE 0 END) / COUNT(DISTINCT customer_id)) * 100, 2) AS immediate_percentage
FROM Delivery
WHERE (customer_id, order_date) IN (
  SELECT customer_id, MIN(order_date)
  FROM Delivery
  GROUP BY customer_id
);
```

- Trong đoạn mã này, chúng ta sử dụng một biểu thức CASE để đếm số lượng đơn đặt hàng ngay lập tức trong số các đơn đặt hàng đầu tiên của mỗi khách hàng. Sau đó, chia cho tổng số lượng khách hàng để tính phần trăm và sử dụng ROUND để làm tròn kết quả đến 2 chữ số thập phân.
