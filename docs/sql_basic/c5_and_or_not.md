# **Thêm giới hạn với `AND`, `OR` hoặc `NOT`**

Okay, chúng ta đã đi qua các kiểu dữ liệu cùng với `WHERE` để tạo filter dữ liệu. Nhưng thực tế thì đâu phải có một filter để lọc dữ liệu mình mong muốn.

## **`AND` để tạo thêm một lớp filter nữa**

Chúng ta sẽ tiếp tục nhìn lại ví dụ về filter trong Excel sau khi đã lọc các chuyến đi của user `iossdk2@opes.com`

![File Excel mẫu](../assets/sql_basic/c3_where_excel_filter.png "File Excel mẫu")

Giả sử, giờ chúng ta muốn chỉ lấy các chuyến kết thúc trong ngày 19/05/2024 của user này, như một người dùng Excel thông thường, chúng ta sẽ filter tiếp ở trường Trip_End_Time và chọn ngày là 2024 -> May -> 19

![File Excel mẫu](../assets/sql_basic/c5_and_or_not_filter_1.png "File Excel mẫu")

Vậy nếu diễn giải ra SQL, chúng ta sẽ làm như thế nào ? Đó là lúc `AND` được sử dụng.

```sql
SELECT
    DISPLAY_NAME,
    TRIP_END_TIME,
    DISTANCE
FROM SAMPLE_EXCEL
WHERE DISPLAY_NAME = 'iossdk2@opes.com'
AND date_trunc('day',TRIP_END_TIME) = date '2024-05-19'
```

Trong lệnh này, do TRIP_END_TIME có kiểu dữ liệu là DATE, nhưng vì đặc thù của vế phải `date '2024-05-19` là tạo ra giá trị cho ngày 19/05/2024 nhưng về mặt giờ thì chỉ tính 0h0p0s, nên để lấy tất cả trong ngày thì về trái phải có thêm phần `date_trunc('day',TRIP_END_TIME)` để cắt phần giờ, phút, giây ra khỏi TRIP_END_TIME nhằm lấy thời gian chính xác nhất để lọc.

## **`OR` để lọc thêm điều kiện**

## **`NOT` để lấy các giá trị không phải giá trị không mong muốn**