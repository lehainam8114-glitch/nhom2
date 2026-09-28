# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_006840.jpg
- L2+R4 center WRONG_CLASS
- R7 mid MISSING
## adasind_036720.jpg
## adasind_056040.jpg
- L5+R5 center ATTRIBUTE
- L1+R2 edge ATTRIBUTE

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 10 | 9 | 1 | 1 |
| mid | 7 | 6 | 1 | 0 |
| edge | 3 | 3 | 0 | 0 |
