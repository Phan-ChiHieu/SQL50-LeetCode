```sql
SELECT
    query_name,
    ROUND(SUM(rating / position) / COUNT(*), 2) AS quality,
    ROUND(SUM(CASE WHEN rating < 3 THEN 1 ELSE 0 END) / COUNT(*) * 100, 2) AS poor_query_percentage
FROM
    Queries
WHERE
    query_name IS NOT NULL  -- Exclude rows with null query_name
GROUP BY
    query_name;

```

1.  Mệnh đề SELECT:

        - query_name: Đây là cột sẽ được sử dụng làm định danh để nhóm kết quả.

        - ROUND(SUM(rating / position) / COUNT(_), 2) AS quality: Tính trung bình chất lượng cho mỗi query_name. Công thức này cộng tổng tỉ lệ rating chia cho position của từng dòng, chia cho tổng số dòng cho query_name đó và làm tròn kết quả đến 2 chữ số thập phân.

        - ROUND(SUM(CASE WHEN rating < 3 THEN 1 ELSE 0 END) / COUNT(\_) \* 100, 2) AS poor_query_percentage: Tính phần trăm câu truy vấn kém (có rating nhỏ hơn 3) cho mỗi query_name. Sử dụng mệnh đề CASE để đếm số dòng có giá trị rating nhỏ hơn 3, chia cho tổng số dòng cho query_name đó, nhân với 100 để lấy phần trăm và làm tròn kết quả đến 2 chữ số thập phân.

2.  Mệnh đề FROM:

        - FROM Queries: Xác định bảng có tên "Queries" từ đó dữ liệu được lựa chọn.

3.  Mệnh đề WHERE:

        -  WHERE query_name IS NOT NULL: Lọc ra các dòng trong đó query_name không phải là null, có nghĩa là chỉ xem xét các dòng mà query_name có giá trị không phải null.

4.  Mệnh đề GROUP BY:

        -   GROUP BY query_name: Nhóm kết quả theo cột query_name. Các hàm tổ hợp (SUM, COUNT) trong mệnh đề SELECT được áp dụng đối với mỗi nhóm riêng lẻ.

Tóm lại, đoạn mã này tính toán chất lượng và phần trăm câu truy vấn kém cho mỗi giá trị query_name không phải null trong bảng "Queries". Nó loại bỏ các dòng với query_name là null và cung cấp kết quả được nhóm theo các giá trị query_name duy nhất.

# ROUND(SUM(CASE WHEN rating < 3 THEN 1 ELSE 0 END) / COUNT(_) _ 100, 2) AS poor_query_percentage

1.  CASE WHEN rating < 3 THEN 1 ELSE 0 END: Đây là một biểu thức CASE, nó đánh giá mỗi dòng trong bảng dữ liệu. Nếu giá trị của cột rating nhỏ hơn 3, nó trả về 1, ngược lại trả về 0. Cụ thể, nếu rating < 3, câu trả lời sẽ là 1, nếu không, là 0.

2.  SUM(...): Tổng hợp giá trị của biểu thức CASE trên cho tất cả các dòng trong nhóm.

3.  / COUNT(\*): Chia tổng trên cho tổng số dòng trong nhóm, đây là để tính trung bình số lần câu trả lời là 1 (tức là số lượng câu truy vấn kém) trên tổng số câu trả lời.

4.  - 100: Nhân kết quả trên với 100 để chuyển đổi thành phần trăm.

5.  ROUND(..., 2): Làm tròn kết quả cuối cùng đến 2 chữ số thập phân.
