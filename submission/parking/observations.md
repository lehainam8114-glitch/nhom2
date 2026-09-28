# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Các vạch sơn ngắn, xiên, nằm giữa hai ô đỗ cạnh nhau —
  (1) các vạch chia ô ở hàng tiền cảnh, đáy ảnh (vạch trắng xiên ở giữa-dưới và bên phải-dưới); (2) các vạch chia ô
  ở hàng thứ hai và thứ ba phía xa hơn. Mỗi polyline chỉ đi theo phần sơn nhìn thấy, dừng ở chỗ vạch hết sơn hoặc
  chạm vạch ngang; không nối qua đoạn mờ/khuất. Các vạch rất nhỏ gần hàng cây phía xa được vẽ ngắn vì độ phân giải thấp.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Không vẽ các dải sơn dài chạy ngang gần hết chiều rộng ảnh
  (nối đầu các ô). Chúng đánh dấu ranh giới giữa dãy ô và lối xe chạy, không chia hai ô đỗ cạnh nhau, nên không thỏa
  định nghĩa `parking_line` trong docs/11. Cũng không vẽ mép bãi/dải cỏ phía xa vì đó là biên bãi, không phải vạch sơn ô.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Polygon bao lối xe chạy trống ở tiền cảnh, giữa hàng ô
  sát máy ảnh và hàng ô kế tiếp. Mép dưới dừng tại đầu các vạch chia ô hàng tiền cảnh, mép trên dừng tại đầu các ô
  hàng kế tiếp; không lấn vào ô đỗ (kể cả ô trống). Hai cạnh trái/phải dừng ở khung ảnh vì lối chạy tiếp tục ra ngoài
  khung. Không có xe hay vật che trong vùng này; chiếc xe đỏ ở xa nằm ngoài polygon.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): Vạch ngang dài nối đầu các ô — là biên ô đỗ hay
  biên lối chạy — tôi chọn không gán `parking_line` nhưng cần người soát xác nhận. Các vạch ở hàng xa gần hàng cây
  mờ và nhỏ, khó xác định điểm kết thúc chính xác.