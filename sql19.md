```sql
# Write your MySQL query statement below
select
    substr(trans_date,1,7) as month,
    country,
    count(id) as trans_count,
    sum(case when state = 'approved' then 1 else 0 end) as approved_count,
    sum(amount) as trans_total_amount,
    sum(case when state = 'approved' then amount else 0 end) as approved_total_amount
from Transactions
group by month, country
```

1. SELECT clause:

   - SUBSTR(trans_date, 1, 7) as month: Tạo một cột mới được đặt tên là "month" bằng cách cắt chuỗi từ cột "trans_date". Chuỗi cắt được chỉ bao gồm 7 ký tự đầu tiên, là năm và tháng của ngày giao dịch.
   - country: Chọn cột "country" từ bảng "Transactions".
   - count(id) as trans_count: Đếm số lượng dòng (giao dịch) cho mỗi nhóm (tháng và quốc gia).
   - SUM(CASE WHEN state = 'approved' THEN 1 ELSE 0 END) as approved_count: Đếm số lượng dòng có trạng thái ('state') là 'approved' cho mỗi nhóm. Sử dụng biểu thức CASE để đếm chỉ khi trạng thái là 'approved'.
   - SUM(amount) as trans_total_amount: Tổng hợp giá trị cột "amount" cho mỗi nhóm, tính tổng số tiền của tất cả các giao dịch.
   - SUM(CASE WHEN state = 'approved' THEN amount ELSE 0 END) as approved_total_amount: Tổng hợp giá trị cột "amount" chỉ cho các giao dịch có trạng thái 'approved'. Sử dụng biểu thức CASE để tính tổng chỉ cho các giao dịch được chấp nhận.

2. FROM clause:

   - FROM Transactions: Xác định bảng "Transactions" từ đó dữ liệu được lựa chọn.

3. GROUP BY clause:
   - GROUP BY month, country: Nhóm kết quả theo cột "month" và "country". Các hàm tổ hợp (COUNT, SUM) trong SELECT clause được áp dụng cho từng nhóm riêng lẻ.
