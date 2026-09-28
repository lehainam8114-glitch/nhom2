# De xuat gold set theo camera - tinh huong gia lap

**Dau bai:** 50.000 frame tu bon camera SVM, ngan sach chon 200 frame de review/gold. Day la tinh huong tren slide,
**khong phai** 50.000 frame co trong repo. Phan bo dung 200 o 45_sampling_plan.csv cho bon camera, moi camera co
normal va hard slice. Gold set o day la **ke hoach tao** reference sau kiem chung, khong phai teaching reference
ADASIND hoac nhan ban vua ve. Neu can, dung notebooks/day11-svm360-colab.ipynb de thu tong phan bo; notebook
khong lam thay phan ly do.

| camera_id | Hard case can chon | Vi sao de sai | Annotation space / calibration can giu | Cach review truoc khi goi la gold |
|---|---|---|---|---|
| front | Xe cat lan, nguoi di bo bat ngo, canh toi | Vung center day vat, de bo sot vat nho; WRONG_CLASS ThreeWheeler/Bus khi vat nho | Box class Car/ThreeWheeler vung center; ego_body khong xuat hien frame front | Hai annotator doc lap, tinh peer agreement >= 85%; Lab Coach xac nhan cac ca WRONG_CLASS |
| rear | Xe may bam sat, xe tai lon che | Ego_body lon che vung giua; truncated kho phan biet | ego_body polygon; box Bike/ThreeWheeler phia sau; lens_border chinh xac | Kiem toi thieu 3 annotator cho ca hard; so sanh box voi model overlay |
| left | Nguoi len xe, xe reo cua re | Rider R03 de nham (nguoi ngoi vs nguoi dat xe); vat bi seam cat | Rider policy (Bike+Pedestrian hay chi Bike); ignore_region crowd | QA kiem R03 rieng; dam bao ca seam duoc flag truoc khi goi la gold |
| right | Xe om, xe buyt o lan phai, nguoi tu cho | ThreeWheeler/Bus nho cuoi khung anh; me vung edge fisheye | box vung edge (r/R>=0.6); truncated do vong kinh | IoU sweep voi nguong 0.5 va 0.7 de chon nguong phu hop vung edge |

- Khi nao can refresh gold set (doi camera, calibration hoac rule): Khi thay camera hardware (tieu cu khac), khi calibration map duoc cap nhat (lech vuong kinh > 5px), hoac khi rule thay doi anh huong >= 10% ca trong gold set hien tai. Viec doi R04 (them R04b ve nguong kich thuoc) can refresh gold set de kiem lai cac ca ThreeWheeler/Bus.

- Mot ca seam/cross-camera can policy va evidence truoc khi ghep hai box: Vat tai seam front-left (goc truoc trai xe): can (a) calibration map xac dinh chinh xac ranh gioi truong nhin; (b) quy dinh camera front la chu neu vat chiem >50% dien tich trong truong nhin front; (c) chi gop box neu co timestamp chung va IoU > 0.3 giua hai camera; (d) flag la cross-camera de QA kiem lai.

- Vi sao peer agreement hoac quality report tren anh mot camera chua chung minh gold set dung cho ca bon camera: Moi camera co goc chup, do me, muc do che khac nhau. Peer agreement tren camera front khong dam bao annotator nhan dang dung vat tai vung edge cua camera rear voi meo fisheye khac. Quality report tren mot camera chi do nhat quan giua annotator trong cung goc nhin, khong bao gom loi do calibration cheo camera hay vung seam.
