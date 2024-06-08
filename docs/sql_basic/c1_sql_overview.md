# **Sơ lược về SQL**

**SQL** là viết tắt của Structure Query Language.

Khi truy vấn dữ liệu từ database, để database hiểu được dữ liệu mà người dùng muốn truy vấn, ta sẽ sử dụng SQL để cho phía database hiểu được mình muốn lấy dữ liệu như thế nào, với điều kiện như nào

**SQL** có dễ tiếp cận không?

Câu trả lời là có, và trong suốt thời gian mọi người sử dụng bộ tài liệu này để truy vấn, mọi người sẽ thấy điều đó.

Về cơ bản, **SQL** có một số đặc điểm sau làm nó dễ tiếp cận

**1. Ngôn ngữ gần với con người**

Mọi người có thể xem ví dụ sau đây:

```sql
SELECT 
    POL_NO,
    POL_EFFECTIVE_DATE,
    POL_EXPIRE_DATE
FROM VIEW_DATASET_CAR_POLICIES;
```

Nếu phiên dịch ra theo đúng ngôn ngữ của chúng ta, thì câu lệnh trên có nghĩa là chúng ta đang muốn lấy số hợp đồng, ngày bắt đầu và ngày kết thúc hiệu lực của hợp đồng trong một kho dữ liệu có tên là `VIEW_DATASET_CAR_POLICIES`

**2. Cấu trúc câu lệnh**

Trong suốt quá trình đọc tài liệu này, mọi người sẽ thấy cấu trúc của các lệnh SQL này sẽ lặp đi lặp lại như sau:

```sql
SELECT
    [...các trường dữ liệu]
FROM [nguồn dữ liệu]
WHERE
    [điều kiện 1]
    AND [điều kiện 2]
    AND [điều kiện 3]
    [... và rất nhiều điều kiện nữa]
ORDER BY [...các trường cần sắp xếp thứ tự];
```

2 đặc điểm này sẽ theo chân mọi người trong suốt quá trình lấy dữ liệu

Tiếp theo: [Câu lệnh SELECT](./c2_select.md)

