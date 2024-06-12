# **Lọc dữ liệu với `IN`**

Chúng ta đã xem qua cách sử dụng `AND`, `OR` hoặc `NOT` để lọc dữ liệu.

Nhưng sẽ như nào nếu điều kiện của chúng ta cần quá nhiều `OR`. Hãy xem ví dụ sau:
```sql
SELECT *
FROM EXAMPLE_EXCEL
WHERE
    POL_NO = '1234'
    OR POL_NO = '5678'
    OR POL_NO = '7890'
    OR POL_NO = '1457'
    OR POL_NO = '2890'
    OR POL_NO = '7824';
```
Ở ví dụ này, chúng ta lọc các hợp đồng có số hợp đồng 1234,5678,7890,1457,2890,7824. Nhưng rất nhiều OR đúng không ?

Giả sử chúng ta rơi vào một tình huống cần tìm khoảng 40 hợp đồng đi. 40 lần OR, gõ cũng mỏi tay phết đấy 😰

Vậy, có các nào để không phải gõ 40 lần `OR` không? Có, đó là lúc `IN` có mặt trong cuộc chơi 😁. Hãy xem nhé

```sql
SELECT *
FROM EXAMPLE_EXCEL
WHERE
    POL_NO IN (
        '1234', '5678', '7890', '1457', '2890', '7824'
    );
```

Thấy thế nào, đơn giản hơn rồi chứ 😏

Vậy khi nào thì sử dụng `IN`? Khi chúng ta cần lấy giá trị của một trường thỏa mãn là có mặt trong một tập giá trị.

Như đã nói từ trước, `SQL` là ngôn ngữ truy vấn gần và thân thiện với con người, nên khi dịch từ `IN` ra thì chúng ta cũng có thể hiểu là trường này phải có giá trị thuộc tập giá trị này mới được lấy.

Thế nếu trong trường hợp mình muốn lấy các giá trị không thuộc tập đó thì sao ?

Như đã nói với mục `NOT`, thì đây chính là nơi `NOT` được sử dụng nhiều và tỏa sáng nhất.

Giả sử cũng là các giá trị trên, nhưng chúng ta không muốn các số hợp đồng đó, thì câu lệnh như sau:

```sql
SELECT *
FROM EXAMPLE_EXCEL
WHERE
    POL_NO NOT IN (
        '1234', '5678', '7890', '1457', '2890', '7824'
    );
```