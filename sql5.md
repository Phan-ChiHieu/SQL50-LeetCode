Table: Tweets

+----------------+---------+
| Column Name | Type |
+----------------+---------+
| tweet_id | int |
| content | varchar |
+----------------+---------+
tweet_id is the primary key (column with unique values) for this table.
This table contains all the tweets in a social media app.

Viết giải pháp để tìm ID của các tweet không hợp lệ. Tweet không hợp lệ nếu số lượng ký tự được sử dụng trong nội dung của tweet lớn hơn 15.

```sql
SELECT tweet_id
FROM Tweets
WHERE LENGTH(content) > 15
```

     - trong MySQL, hàm để lấy độ dài của một chuỗi là CHAR_LENGTH() hoặc LENGTH()
