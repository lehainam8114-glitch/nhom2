# Ke hoach review tu loi quan sat duoc

Tu findings.csv va zone_table.md, chon **hai lat cat cua bai ADASIND mot camera** can review truoc. Bang nay
giai thich du lieu that ban vua lam; no khong thay cho ke hoach bon camera gia lap o 45_sampling_plan.csv.

| Lat cat / frame | So ca va loai loi | Vi sao review truoc | Bang chung can giu |
|---|---|---|---|
| adasind_006840.jpg (B1-center) | 5 MISSING (R4, R7, L8+R1...) + 1 WRONG_CLASS + 6 M_only SPURIOUS | Frame nay co nhieu loi nhat (P1 rework); WRONG_CLASS va MISSING anh huong toi recall; can xac nhan sau rework loi giam | findings.csv dong r1_craft + r3_diag cho frame nay; rework/delta.md center matched 9->10 |
| adasind_056040.jpg (B1-center) | 2 ATTRIBUTE (L5+R5, L1+R2) + 6 M_only SPURIOUS | ATTRIBUTE truncated sai lien tuc o hai vat; co the la van de he thong trong cach nhan dang vung rim vong kinh | findings.csv dong r1_craft L5+R5 va L1+R2; selfqc canh bao truncated khac du kien |

Gioi han cua ket luan tu ba frame ADASIND: Ba frame qua it de ru ra xu huong tong quat; ket qua co the bi lech do mot frame co nhieu loi (006840) chi phoi so lieu. Khong the ket luan ty le loi theo class hay zone ma khong co them du lieu.

## Chuyen sang ke hoach bon camera gia lap

Cach soat do phu cua 200 frame o 45_sampling_plan.csv: phan bo deu cho 4 camera x 2 loai (normal/hard), uu tien camera front va rear vi co the gap vat cat qua nhau nhieu nhat. Tranh chon nhieu frame lien nhau trong cung canh (vi du 5 frame lien tiep tren pho vang se dem la 5 ca nhung thuc chat chi la 1 tinh huong).
Vi sao ke hoach do chi giup tim ca can soi, chua do duoc ty le loi: 200/50000 = 0.4% sample, khong du dai dien thong ke; frame duoc chon co the co bias (chon hard case nhieu hon) khong phan anh ty le loi thuc trong toan bo dataset.
