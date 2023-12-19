Bảng "Customer" có các cột sau:

id (int): Là khóa chính của bảng, có giá trị duy nhất cho mỗi khách hàng.
name (varchar): Là tên của khách hàng, kiểu dữ liệu là varchar (chuỗi ký tự).
referee_id (int): Là id của khách hàng người giới thiệu (người đã giới thiệu khách hàng hiện tại). Đây là khóa ngoại tham chiếu đến cột "id" trong bảng "Customer".
Yêu cầu đề bài là tìm tên của những khách hàng không được giới thiệu bởi khách hàng có id = 2. Điều này có nghĩa là chúng ta cần tìm những khách hàng có cột "referee_id" không bằng 2 hoặc có giá trị NULL (nếu không có người giới thiệu).

```sql
SELECT name
FROM Customer
WHERE referee_id <> 2 OR referee_id IS NULL;
```

    Trong truy vấn này:

        - SELECT name: Chọn cột "name" để hiển thị trong kết quả.
        - FROM Customer: Xác định bảng là "Customer".
        - WHERE referee_id <> 2 OR referee_id IS NULL: Chỉ chọn các dòng trong đó cột "referee_id" không bằng 2 hoặc có giá trị NULL (không có người giới thiệu).

## Cú pháp <> và IS NULL

    - <> là một phép so sánh khác không bằng. Nó được sử dụng để kiểm tra xem hai giá trị có khác nhau hay không. Nếu giá trị bên trái của <> không bằng giá trị bên phải, điều kiện sẽ trả về true; ngược lại, nếu chúng bằng nhau, điều kiện sẽ trả về false.
    
    - IS NULL là một điều kiện sử dụng để kiểm tra xem giá trị của một cột có là NULL hay không. NULL thường được sử dụng để biểu diễn giá trị thiếu hoặc không có dữ liệu trong một cột.
