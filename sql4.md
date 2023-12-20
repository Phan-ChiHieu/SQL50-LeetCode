Bảng: Views

+---------------+---------+
| Tên cột | Loại |
+---------------+---------+
| article_id | int |
| author_id | int |
| viewer_id | int |
| view_date | date |
+---------------+---------+

Không có khóa chính (cột có giá trị duy nhất) cho bảng này, bảng có thể có các hàng trùng lặp.
Mỗi hàng của bảng này cho biết một số người xem đã xem một bài viết (được viết bởi một số tác giả) vào một ngày nào đó.
Lưu ý rằng author_id và viewer_id giống nhau đồng nghĩa với việc cùng một người.

Viết một giải pháp để tìm tất cả các tác giả đã xem ít nhất một trong những bài viết của chính họ.

Trả về bảng kết quả được sắp xếp theo id theo thứ tự tăng dần.

```sql
SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY id;

```

    - DISTINCT: được sử dụng để loại bỏ các bản ghi trùng lặp từ kết quả truy vấn. Nó sẽ chỉ hiển thị các giá trị duy nhất của cột hoặc các giá trị duy nhất của các cột được liệt kê trong phần SELECT
    - ORDER BY trong SQL được sử dụng để sắp xếp kết quả của một truy vấn theo một hoặc nhiều cột. Bạn có thể sắp xếp kết quả theo thứ tự tăng dần (mặc định) hoặc thứ tự giảm dần.

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...;

```

Trong đó:

    - column1, column2, ...: Các cột mà bạn muốn hiển thị trong kết quả.
    - table_name: Tên bảng từ nơi bạn muốn lấy dữ liệu.
    - ORDER BY column1 [ASC|DESC], column2 [ASC|DESC], ...: Xác định cột hoặc các cột mà bạn muốn sắp xếp và thứ tự sắp xếp (tăng dần hoặc giảm dần).
    - Ví dụ, để sắp xếp kết quả theo thứ tự giảm dần của cột column1, bạn có thể sử dụng ORDER BY column1 DESC
