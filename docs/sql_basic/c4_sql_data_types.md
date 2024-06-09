# **Các kiểu dữ liệu trong SQL**

Trước khi đi vào mục tiếp theo, chúng ta sẽ cần điểm qua một vài kiểu dữ liệu thông dụng trong SQl.

Mục đích của mục này là để mọi người có thể hình dung SQL có những kiểu dữ liệu nào, nếu cần đặt điều kiện thì sẽ cần viết như nào để có thể đặt điều kiện cho đúng

Các kiểu dữ liệu trong SQL bao gồm 3 kiểu chính

| Kiểu dữ liệu | Diễn giải | Ví dụ |
| ------------ | --------- | ------|
| NUMBER | Số học | `35` |
| VARCHAR | Chuỗi ký tự | `'iossdk2@opes.com'` |
| DATE | Ngày giờ | `date '2024-05-01'`|

**Trong đó:**

- `NUMBER` là các số mà trong cuộc sống chúng ta thường thấy

- `VARCHAR` là các chuối ký tự, được bắt đầu với dấu `'` và kết thúc với dấu `'`

- `DATE` là kiểu ngày, tuy nhiên đây là kiểu phức tạp nhất do tùy vào loại database mà sẽ có kiểu lấy khác nhau. Tuy nhiên, để dễ dàng cho mọi người thì sẽ thống nhất 1 kiểu trong tài liệu này là `date 'yyyy-mm-dd'`