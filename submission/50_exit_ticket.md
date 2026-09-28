# Exit ticket

Doc docs/10-svm360-reading-vi.md truoc khi tra loi cau 1-2. Cac cau ve zone, why, rework, parking va sampling
da nam trong file tuong ung nen khong hoi lai o day.

1. Mot vat o vung seam giua hai camera that xuat hien voi hai box khac nhau: do la loi DUPLICATE hay can mot quy
   tac rieng? Vi sao?
   Khong phai tu dong la DUPLICATE. Mot vat tai seam co the hien hop le tren ca hai camera vi moi camera chup goc nhin khac nhau; day la tinh huong cross-camera binh thuong. DUPLICATE chi khi cung mot camera tao hai box cho cung mot vat trong cung frame. Can mot policy seam rieng: xac dinh vung chong lap (overlap zone) cua hai camera, quy dinh camera nao la chu (primary), va chi box tren camera chu; camera phu chi box khi vat hoan toan nam trong truong nhin cua no ma khong chong lan camera chu. Bằng chứng cần: calibration map xac dinh ranh gioi truong nhin chinh xac truoc khi quyet dinh.

2. Mot vat di qua nhieu frame tren cung camera: khi nao giu cung track ID, khi nao them keyframe hoac trang thai Outside?
   Giu cung track ID khi vat con nhin thay lien tuc tren cung camera (khong bi che hoan toan). Them keyframe khi vi tri, kich thuoc hoac attribute thay doi dang ke giua cac frame (vi du xe reo, nguoi xoay nguoi). Dat trang thai Outside khi vat di ra ngoai truong nhin hoac bi che 100% (theo sau boi Outside=True), roi dat lai khi vat quay lai truong nhin. Bang chung can truoc khi noi track qua hai camera: (a) timestamp/frame ID chung; (b) calibration xac nhan cung vat vat ly; (c) track ID nhat quan giua hai camera theo thoa thuan truoc.

3. Nhin lai ca buoi: mot cho ban tin nhan minh dung nhung reference hoac nguoi soat nghi khac (dan frame/object_ref),
   ban da xu ly the nao, va neu lam lai slice nay ban se doi gi trong cach lam?
   Ca: adasind_006840.jpg L2 - toi gon nhan Bus vi nhin thay hinh dang dai, nhung reference (R4) va QA deu cho la ThreeWheeler. Toi xem lai anh ky hon va dong y voi ThreeWheeler vi box nho (~60x70px) khong phu hop xe buyt; da rework trong P5. Neu lam lai: zoom vao tung vat truoc khi gon nhan, kiem cheo voi R04 ngay khi ve box thay vi cho den QA moi phat hien; va dung checklist tu soat sau moi frame thay vi sau khi lam het ca ba frame.
