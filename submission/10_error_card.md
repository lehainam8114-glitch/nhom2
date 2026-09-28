# Error analysis card

## Zone x block

| zone | block | what | count |
|---|---|---|---:|
| center | B1 | ATTRIBUTE | 1 |
| center | B1 | MISSING | 5 |
| center | B1 | SPURIOUS | 6 |
| center | B1 | WRONG_CLASS | 1 |
| center | C0 | BOX_GEOMETRY | 1 |
| center | C0 | SPURIOUS | 1 |
| edge | B1 | ATTRIBUTE | 1 |
| edge | B1 | MISSING | 2 |
| edge | B1 | SPURIOUS | 5 |
| mid | B1 | MISSING | 4 |
| mid | B1 | SPURIOUS | 6 |
| mid | C0 | BOX_GEOMETRY | 1 |
| unknown | B1 | MISSING | 3 |

## Top defects
- SPURIOUS: 18 (vi du frame adasind_006840.jpg M_only)
- MISSING: 14 (vi du frame adasind_006840.jpg R4, R7)
- BOX_GEOMETRY: 2 (vi du frame adasind_019560.jpg)

## Phan tich cua ban

Hai bang tren do python3 lab11.py card tinh tu findings.csv; chay lai lenh se cap nhat bang va giu nguyen muc nay.

- Nguyen nhan kha di (why) va vi sao ban nghi vay:
  SPURIOUS nhieu nhat (18): phan lon la M_only do model YOLO26m huan luyen tren anh phang khong quen fisheye, sinh false positive o moi zone (center 6, mid 6, edge 5). Theo iou_sweep.md, M spurious tang nhanh khi tang nguong IoU len 0.7 (mid tang tu 6 len 9). Bang chung: 18 dong findings.csv why=E4_model_domain.
  MISSING (14): annotator bo sot vat nho gan nguong H=40 (frame 006840 R4 ThreeWheeler, R7 Pedestrian) va nham class (L2 Bus phai la ThreeWheeler). Bang chung: r1_craft L2+R4 WRONG_CLASS rule_id=R04, r3_diag R4 R_only.

- Cach sua va ai nhan viec (owner):
  SPURIOUS M_only (18 ca): khong sua nhan vi la loi model E4; owner=annotator ghi keep_with_reason cho toan bo.
  MISSING + WRONG_CLASS P1 (r1_craft, r3_diag): annotator da rework trong P5: doi L2 tu Bus sang ThreeWheeler, ve them box R4. Ket qua: center matched tang tu 9 len 10 (rework/delta.md).

- Bang chung (anh trong screenshots/, dong findings, rule):
  findings.csv dong r1_craft L2+R4 WRONG_CLASS rule_id=R04; 18 dong r3_diag M_only why=E4_model_domain; rework/delta.md center matched 9->10 sau P5.
