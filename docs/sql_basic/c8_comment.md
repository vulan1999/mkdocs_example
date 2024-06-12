# **Tạo Comment trong SQL**

Trước khi đi tiếp vào nội dung kế có phần nâng cao hơn, chúng ta sẽ cần biết một tính năng quan trọng bậc nhất của SQL, đó là comment

Comment sẽ có cú pháp : `--` + `lời nhắn`

Tại sao tính năng này quan trọng ? Nó quan trọng vì đây là một thứ để giúp chúng ta note lại những thứ cần thiết, hoặc đánh dấu lại một số đoạn khó hiểu nhưng không ảnh hưởng đến quá trình chạy lệnh.

Ví dụ:

```sql
-- Chọn tất cả dữ liệu từ bảng EXAMPLE
SELECT * FROM EXAMPLE
```

Thấy vùng chữ xám chứ. Nó sẽ không chạy nếu chúng ta chạy lệnh đâu.

Nhưng cũng còn một cách khác để comment đó là bắt đầu bằng `/*` và kết thúc bằng `*/`.

Thế ơ vậy tại sao không phải có một cách mà lại tận 2 cách.

Cách này hay ở chỗ này nè.

```sql
/*
    Script này được viết bởi Lân
    Có gì cứ hỏi thằng Lân vì nó viết cái này
    Theo giải thích thì đây là lệnh lấy hết dữ liệu từ nơi lưu dữ liệu sản phẩm CAR
*/
SELECT * FROM POLICY_CAR
```

```sql

--    Script này được viết bởi Lân
--    Có gì cứ hỏi thằng Lân vì nó viết cái này
--    Theo giải thích thì đây là lệnh lấy hết dữ liệu từ nơi lưu dữ liệu sản phẩm CAR
SELECT * FROM POLICY_CAR
```

Điểm khác biệt của việc sử dụng cặp `/*` và `*/` là chúng có thể giúp comment nhiều dòng mà không cần mất công gõ `--` ở mỗi dòng.
Cách này giúp tiết kiện thời gian và công sức cho người cần note nhiều.