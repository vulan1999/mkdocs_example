# **Câu lệnh `SELECT`**

## **Giới thiệu về `SELECT` và `FROM`**
Câu lệnh `SELECT` có thể nói là câu lệnh cở bản nhất trong **SQL**

Để cho mọi người hiểu rõ hơn, hãy xem ví dụ sau:
```sql
SELECT
    POL_NO,
    POL_EFFECTIVE_DATE,
    POL_EXPIRE_DATE
FROM VIEW_DATASET_PA_POLICIES_IDIT;
```

Như ở mục trước, mọi người cũng đã thấy 1 ví dụ lấy dữ liệu như này.

Câu lệnh sẽ được giải thích như sau:

- Đầu tiên, chúng ta sử dụng từ khóa `SELECT` để liệt kê các trường dữ liệu cần lấy

- Khi biết dữ liệu cần lấy rồi, vậy `FROM` để làm gì? Thực tế thì `SELECT` và `FROM` luôn là một cặp của lệnh. `FROM` là để định nghĩa nguồn dữ liệu cần lấy, trong trường hợp của ví dụ này là **`VIEW_DATASET_PA_POLICIES_IDIT`**

## **Cách lấy nhanh tất cả các trường từ nguồn dữ liệu**

Nếu chỉ cần liệt kê thì cũng đơn giản đúng không ? Nhưng chuyện gì sẽ xảy ra khi mọi người muốn lấy tất cả các trường của nguồn dữ liệu, nhưng lại ngại phải liệt kê tên trường như này ?

Chúng ta sẽ xem ví dụ sau để hiểu rõ hơn:
```sql
SELECT
    CLAIM_NO,
    CLAIM_POLICY_NO,
    CLAIM_POLICY_EFFECTIVE_DATE,
    CLAIM_POLICY_EXPITE_DATE,
    CLAIM_REQUEST_DATE,
    CLAIM_OPEN_DATE,
    CLAIM_STAFF,
    CLAIM_SUBMISSION_DATE,
    CLAIM_APPROVED_DATE,
    CLAIM_PAYMENT_DATE,
    CLAIM_REQUEST_AMOUNT,
    CLAIM_REDUCE_AMOUNT,
    CLAIM_ACTUAL_AMOUNT,
    CLAIM_BENEFICIARY
FROM CLAIMS
```

Đây là một ví dụ về nhiều trường, nhưng ví dụ này vẫn còn ít trường để mọi người thực sự thấy nản khi phải liệt kê các trường. Câu hỏi là: Nếu mọi người gặp phải một nguồn dữ liệu có tầm 50, hoặc 100, hoặc ghê gớm hơn là 150 trường, mọi người sẽ tiếp tục liệt kê?

Câu trả lời rõ ràng là **Không** to và rõ ràng rồi. Vậy có cách nào để không phải làm công đoạn tốn thời gian này không ?

Câu trả lời dĩ nhiên là có, và ví dụ là đây:
```sql
SELECT *
FROM CLAIMS
```

Dấu `*` mọi người có thể hiểu giống như một câu select all từ nguồn dữ liệu.

Tại sao lại là dấu `*` trong khi có thể sử dụng từ `all`? Về câu hỏi này thì nếu trên góc độ kỹ thuật và kinh nghiệm sử dụng thì có thể giải thích như sau:

- `all` có thể là tên của 1 trường dữ liệu trong bảng

- Do đặc thù kỹ thuật của ngôn ngữ

## Tổng kết

Well, tóm lại thì cấu trúc lệnh sau mục này có thể tổng kết như sau:

```sql
SELECT
    [...danh sách các trường cần lấy]
FROM [nguồn dữ liệu]
```

hoặc nếu muốn lấy tất cả các trường từ nguồn dữ liệu

```sql
SELECT *
FROM [nguồn dữ liệu]
```

Tiếp theo: [Đặt điều kiện giới hạn dữ liệu với `WHERE`](./c3_where.md)

