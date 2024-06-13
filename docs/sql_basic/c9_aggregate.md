# **Các hàm tổng hợp dữ liệu**

Okay, chúng ta đã đi qua hết các phần cơ bản của SQL qua các phần trước.
Giờ chúng ta sẽ ngó qua các hàm tổng hợp dữ liệu.

Dành cho người không biết tổng hợp dữ liệu là gì: Nó có thể là tính tổng của 1 tập dữ liệu, hoặc tính phí trung bình của phần dữ liệu của 1 tháng, hoặc đơn giản hơn là đếm xem có bao nhiêu bản ghi, hay tìm số lớn nhất và bé nhất trong một trường.

Trong SQL có 5 hàm thông dụng:

- `SUM` : tính tổng

- `MAX`: tìm giá trị lớn nhất

- `MIN`: tìm giá trị bé nhất

- `AVG`: tính giá trị trung bình

- `COUNT`: đếm số lượng

Ví dụ chúng ta có một tập dữ liệu sau:

| POL_NO | POL_FEE |
| ------------|--------------|
| 880890832 | 60000 |
| 801830298 | 132000 |
| 907408403 | 60500 |
| 890832321 | 40000 |
| 808041321 | 55000 |
| 732434234 | 70000 |

Đếm số lượng bản ghi sử dụng `COUNT`:
```sql 
SELECT COUNT(*) FROM EXAMPLE; --6
```

Tìm phí lớn nhất trong ví dụ:
```sql
SELECT MAX(POL_FEE) FROM EXAMPLE; --132000
```

Tìm phí thấp nhất trong ví dụ:
```sql
SELECT MIN(POL_FEE) FROM EXAMPLE; --40000
```

Tính tổng phí bảo hiểm trong ví dụ:
```sql
SELECT SUM(POL_FEE) FROM EXAMPLE; --417500
```


Tính phí trung bình trong ví dụ:
```sql
SELECT AVG(POL_FEE) FROM EXAMPLE; --69583.33
```

Tuy nhiên, đây là ví dụ đơn giản để mọi người hiểu. Thực tế, khi tổng hợp dữ liệu thì mọi người sẽ luôn muốn thống kê như sau:

| Loại sản phẩm | Số lượng đơn | Tổng phí |
| ------------- | ------------ | -------- |
| OCAR | 2 | 200,000,000 |
| TPL | 5 | 300,000 |
| HOME | 1 | 400,000,000 |

Để làm được điều này, hãy xem ví dụ về dữ liệu gốc sau:

| product | fee |
| ------------- | -------- |
| OCAR | 150,000,000 |
| TPL | 60,000 |
| HOME | 400,000,000 |
| TPL | 60,000 |
| TPL | 60,000 |
| TPL | 60,000 |
| OCAR | 50,000,000 |
| TPL | 60,000 |

Để tổng hợp kết quả như trên, chúng ta sẽ có một đoạn `GROUP BY` đằng sau. Mục đích của `GROUP BY` là để SQL hiểu chúng ta muốn tổng hợp theo nhóm giá trị nào để kết quả trả ra có thể theo nhóm giá trị đó.

SQL sẽ như sau:
```sql
SELECT product, count(pol_no), sum(fee)
FROM EXAMPLE
GROUP BY product
```

Cấu trúc SQL với tổng hợp như sau:

```sql
SELECT trường_1, trường_2, trường_3,...,trường_n,
    tổng_hợp_1, tổng_hợp_2, tổng_hợp_3,...,tổng_hợp_n
FROM bảng
GROUP BY trường_1, trường_2, trường_3,...,trường_n

```
