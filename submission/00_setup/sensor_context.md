# Sensor context

- Rig: Một camera fisheye duy nhất, nhìn về **phía trước** theo chiều di chuyển, ảnh dọc (portrait). Theo quan sát,
  camera gắn thấp, khoảng ngang tay lái của một **xe hai bánh**: bóng đổ trên mặt đường ở frame 019560 có dáng người
  ngồi trên xe máy, và ở 036720/056040 thấy tay/áo người lái ở mép trái dưới. Cảnh là đường hai làn ở khu dân cư/đô
  thị nhỏ (Ấn Độ), nhiều xe máy, auto-rickshaw (ThreeWheeler), người đi bộ sát lề; ban ngày, có frame bị ngược sáng
  và lóa (056040). ADASIND không kèm tài liệu rig, nên vị trí gắn và độ cao chỉ là suy luận từ ảnh. Dữ liệu chỉ có
  **một camera**, không đại diện cho bốn camera front/rear/left/right của hệ SVM và không có calibration hay seam.
- `ego_body` nhìn thấy ở đâu trong frame: Ở **mép trái và góc dưới trái** bên trong vòng kính — phần tay/áo của
  người lái, tay lái hoặc thân xe hai bánh (rõ ở 036720, 056040; ở 019560 là vật tối sát mép trái cùng bóng đổ của
  xe/người lái trên mặt đường — bóng đổ không phải ego_body). Frame **006840 không thấy thân xe ego** nên không vẽ
  polygon `ego_body` cho frame này. Vị trí và kích thước phần ego thay đổi giữa các frame vì người lái cử động.
- Vòng kính (lens circle): Vòng tròn nằm ở **giữa khung**, hơi lệch lên trên; đường kính gần bằng toàn bộ chiều
  ngang ảnh nên **bị khung cắt nhẹ ở mép trái và mép phải**. Ngoài vòng là vùng tối ở **phía trên** (dải mỏng) và
  **phía dưới** (dải dày hơn), cộng bốn góc. Vòng chiếm khoảng 100% chiều ngang và ~85% chiều cao khung hình. Rìa vòng
  méo mạnh: dây điện, mép đường và vật ở rìa bị kéo cong, vật gần rìa dễ bị `truncated` bởi vòng kính.