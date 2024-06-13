# **Lọc dữ liệu tổng hợp cùng `HAVING`**

Chúng ta sẽ cùng nhìn lại ví dụ đã được tổng hợp ở phần trước:

| Loại sản phẩm | Số lượng đơn | Tổng phí |
| ------------- | ------------ | -------- |
| OCAR | 2 | 200,000,000 |
| TPL | 5 | 300,000 |
| HOME | 1 | 400,000,000 |


Sau khi tổng hợp dữ liệu xong, nhiều người có lẽ sẽ muốn đặt điều kiện thêm như: Giờ tôi có tổng phí bảo hiểm rồi, có thể lấy giúp tôi các sản phẩm có phí trên 500000 được không ?

Được, nhưng làm thế nào? Chúng ta sẽ làm như sau:

```sql
SELECT * FROM (
    SELECT product, count(pol_no) as pol_count, sum(fee) as sum_fee
    FROM EXAMPLE
    GROUP BY product
)
WHERE sum_fee > 500000;
```
Lệnh này giải thích như sau:

Ta sẽ thấy 2 câu `SELECT` đúng không ? Vậy ta sẽ đi từ trong ra ngoài.

Câu `SELECT` bên trong là câu lệnh mà ta đã nhìn thấy ở phần trước có nhiệm vụ tổng hợp dữ liệu từ file. Nhưng từ `AS` thì chưa thấy có. Từ `AS` ở đây đóng vai trò như một nhãn mà chúng ta gọi cho trường đó. Ở đây, ta đánh nhãn cho phần tổng hợp dữ liệu có tên là pol_count cho số lượng hợp đồng của sản phẩm và sum_fee cho tổng phí bảo hiểm của sản phẩm.

Dữ liệu sau câu `SELECT` sẽ trông như sau:

| product | pol_count | sum_fee|
| ------------- | ------------ | -------- |
| OCAR | 2 | 200,000,000 |
| TPL | 5 | 300,000 |
| HOME | 1 | 400,000,000 |

Tiếp theo, câu `SELECT` ở mặt ngoài có vai trò là lấy dữ liệu từ nguồn là kết quả của câu `SELECT` được thực hiện phía trong, với phía trong được phân cách bởi cặp `(` và `)` trước từ khóa `FROM` và `WHERE` ở bên ngoài để đặt điều kiện để lấy dữ liệu.

Kết quả của câu `SELECT` thứ hai như sau:
| product | pol_count | sum_fee|
| ------------- | ------------ | -------- |
| OCAR | 2 | 200,000,000 |
| HOME | 1 | 400,000,000 |

Nhưng ơ, tiêu đề của mục là `HAVING` mà nhỉ ?

Đúng, nhưng qua ví dụ này, mọi người chắc hẳn sẽ thấy chúng ta phải làm thêm một động tác `SELECT` lồng trong `SELECT` để lấy kết quả mình muốn từ một kết quả tổng hợp, khiến câu lệnh nó hơi lằng nhằng một chút. Tuy nhiên, SQL cũng có phần vạn năng của nó, và đó là sử dụng `HAVING` để lọc dữ liệu tổng hợp như này.

Câu lệnh trên khi sử dụng `HAVING` sẽ như sau:
```sql
SELECT product, count(pol_no) as pol_count, sum(fee) as sum_fee
FROM EXAMPLE
GROUP BY product
HAVING sum(fee) > 500000;
```

Ngắn hơn rất nhiều và dễ hơn đúng không ?

Cấu trúc khi sử dụng `HAVING` như sau:

```sql
SELECT trường_1, trường_2, trường_3,...,trường_n,
    tổng_hợp_1, tổng_hợp_2, tổng_hợp_3,...,tổng_hợp_n
FROM bảng
GROUP BY trường_1, trường_2, trường_3,...,trường_n
HAVING tổng_hợp_x > điều kiện ( < điều kiện, = điều kiện)

```