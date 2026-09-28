# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (LR_noM + R_only) | M thừa (LM_noR + M_only) | Lỗi L chính (what) |
|---|---:|---:|---:|---:|---:|---|
| center | 10 | 1 | 1 | 5 | 6 | WRONG_CLASS (1) |
| mid | 7 | 1 | 0 | 3 | 6 | MISSING (1) |
| edge | 3 | 0 | 0 | 2 | 5 | ATTRIBUTE (1) |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên:
  Người (L): zone center gãy nhiều nhất — 1 missing, 1 spurious, 1 WRONG_CLASS. Zone mid có 1 missing. Zone edge không có missing/spurious nhưng có 1 lỗi ATTRIBUTE.
  Model (M): zone center gãy nặng nhất — 5 missing + 6 thừa. Zone mid: 3 missing + 6 thừa. Zone edge: 2 missing + 5 thừa. Model thừa đồng đều ở cả ba zone.

- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu ego_body, ...) và giới hạn của slice ba frame:
  Người (L): WRONG_CLASS ở center có thể do khó phân biệt lớp xe khi méo fisheye vùng trung tâm; MISSING ở mid do vật nhỏ gần ngưỡng H=40 dễ bỏ sót; ATTRIBUTE ở edge do truncated/occluded khó phán đoán khi vật bị cắt vòng kính.
  Model (M): số thừa (M_only) rất cao ở mọi zone — giả thuyết model huấn luyện trên ảnh phẳng, không quen méo fisheye nên tạo nhiều false positive ở vùng rìa và kể cả center; tuy nhiên chỉ có 3 frame nên không đủ để kết luận xu hướng toàn bộ dataset.
