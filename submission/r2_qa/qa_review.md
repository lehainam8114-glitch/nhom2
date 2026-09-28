# QA review · B1-center

Mã khóa: 16ED-3B88

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_006840.jpg | L8 | R03 | L8 ThreeWheeler thiếu box cho người lái bên trong xe (cần kiểm tra lại với R03 xem người ngồi trong phương tiện và người đứng sát bên trái L8 có vẽ box riêng không). |
| adasind_036720.jpg | missing_cars | R01 | Thiếu box cho các xe Car ở phía xa trên trục đường (cần đối chiếu ngưỡng chiều cao H >= 40px theo R01). |
| adasind_056040.jpg | missing_bike | R09 | Thiếu box / nhãn cho người đi xe máy ở bên trái góc dưới khung hình (cần kiểm tra xem box có đè quá 50% vào vùng ignore_region ). |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.