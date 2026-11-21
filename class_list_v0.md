## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` (`seat`, `seatbelt`) | `seat`: driver · `seatbelt`: worn_correct / worn_incorrect / not_worn / unknown | Xác nhận vị trí người lái và phát hiện chưa thắt dây hoặc thắt dây sai quy cách (luồn dưới nách, sau lưng) để cảnh báo an toàn trước khi xe chạy | Có (thấy rõ tư thế người và dải dây an toàn nhờ phản xạ NIR, trừ khi bị áo dày hoặc tay che) |
| 2 | `face` & `glasses` | box khuôn mặt · `glasses`: unknown / none / clear / sun | Định vị vùng mặt tài xế làm cơ sở cắt vùng xử lý mắt/điểm mốc; nhận biết loại kính để điều chỉnh ngưỡng cảnh báo và xử lý nhiễu phản xạ | Có thấy mặt; trên NIR kính râm có thể nhìn xuyên qua như kính thường hoặc xuất hiện đốm lóa LED |
| 3 | `eye_left`, `eye_right` | open / closed / unknown | Theo dõi trạng thái đóng/mở từng mắt theo thời gian thực để phát hiện buồn ngủ, chớp mắt kéo dài hoặc mất ý thức khi lái xe | Có, trừ khi bị đốm phản xạ LED trên tròng kính, góc nghiêng mặt hoặc vùng tối che khuất |
| 4 | `gaze_zone` | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Xác định hướng chú ý của tài xế nhằm phát hiện xao nhãng thị giác (nhìn xuống đùi, nhìn màn hình trung tâm quá lâu thay vì nhìn đường/gương) | Có (ước lượng qua hướng đầu và vị trí đồng tử, trừ khi tròng kính tối hoặc phản xạ che mắt) |
| 5 | `face13` | 13 điểm mốc mặt (cờ `occluded` / `outside`) | Tính toán góc xoay đầu 3D (pitch, yaw, roll), độ mở mí mắt (EAR) và độ mở miệng (ngáp) phục vụ cảnh báo mệt mỏi | Có (khi khuôn mặt rộng $\ge 60\text{ px}$ và không bị tay, chai nước hoặc góc nghiêng che khuất) |
| 6 | `hand` (`whose`, `side`, `on_wheel`) | `whose`: driver / passenger · `side`: left / right · `on_wheel`: yes / no / unknown | Kiểm tra mức độ sẵn sàng tiếp quản tay lái của tài xế trong xe tự hành và phát hiện hành vi rời tay khỏi vô lăng | Có (nhận diện qua hình dạng bàn tay và vị trí tiếp xúc với vô lăng) |
| 7 | `phone` (`state`) | held / mounted / lap | Phát hiện hành vi cầm điện thoại nghe gọi, nhắn tin hoặc đặt trên đùi gây mất tập trung nghiêm trọng khi điều khiển xe | Có (nhận diện qua hình khối chữ nhật, cạnh viền hoặc ánh sáng phát ra từ màn hình) |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` (`seat`) | rear_left / rear_middle / rear_right (theo chiều xe) | Đếm số lượng và xác định đúng vị trí ngồi của từng hành khách để điều chỉnh lực bung túi khí theo ghế và phát hiện người còn sót lại trên xe | Có (thấy rõ hình khối cơ thể hành khách trên từng vị trí ghế) |
| 2 | `person.seatbelt` | worn_correct / worn_incorrect / not_worn / unknown | Cảnh báo nhắc nhở hành khách hàng ghế sau chưa cài dây an toàn hoặc cài sai tư thế khi xe đang lưu thông | Có (thấy rõ dải dây chéo qua vai, trừ khi trùng màu áo tối hoặc khuất trong bóng tối) |
| 3 | `face` (OMS) | rectangle (chỉ vẽ box) | Xác định vị trí vùng đầu hành khách để đánh giá tư thế ngồi (nằm ngả, cúi thấp sát ghế trước) nhằm tránh chấn thương khi túi khí bung | Có (trừ khi hành khách quay mặt ra sau hoặc cúi gằm mặt) |
| 4 | `child_seat` (`occupied`) | `seat` · `occupied`: no / unknown | Nhận diện ghế trẻ em lắp trên xe và trạng thái trống/bị che phủ để vô hiệu hóa túi khí ghế tương ứng hoặc kích hoạt radar kiểm tra trẻ bị bỏ quên | Có (nhìn rõ khung ghế và lòng ghế trống ngay cả trong điều kiện ảnh RGB bị thiếu sáng) |
| 5 | `infant_seat` (`facing`) | `seat` · `facing`: rear / front | Phát hiện nôi xách em bé và hướng lắp (quay ngược về sau hay quay xuôi ra trước) để bắt buộc ngắt túi khí, ngăn nguy cơ túi khí bung trực diện vào nôi | Có (phân biệt qua hình dạng vỏ nhựa lưng nôi hoặc mặt đệm ngồi bên trong) |
| 6 | `object` (`type`) | `seat` · `type`: bag / box / cup / other | Phân biệt hành lý, đồ vật đặt trên ghế với người thật, giúp loại bỏ cảnh báo thắt dây an toàn giả hoặc báo động bỏ quên người nhầm từ cảm biến trọng lượng | Có (nhận diện qua hình dáng vật thể trong bóng tối tốt hơn RGB nhưng mất thông tin màu sắc) |
| 7 | `frame_meta` | `modality`: rgb / ir · `light`: day / night / unknown · `camera_blocked`: yes / no | Kiểm soát chất lượng luồng dữ liệu đầu vào; cảnh báo hệ thống mất khả năng giám sát cabin khi ống kính camera bị che khuất (`camera_blocked = yes`) | Có (xác định trạng thái chiếu sáng hồng ngoại và phát hiện vật cản che kín ống kính) |

## 2 câu hỏi leo thang

1. Câu hỏi: Trong bộ dữ liệu OMS thực tế (mở rộng từ SVIRO), khi có trẻ em ngồi bên trong `child_seat`, schema chuẩn của dự án sẽ gán theo trạng thái ghế (`occupied = yes`) hay vẽ lồng thêm một box `person` (kèm thuộc tính độ tuổi) cho đứa trẻ bên trong?
   Khung ví dụ: `S05_rgb.png` (và `S02_rgb.png`)
   Bạn tạm gán thế nào và vì sao: Hiện tại trên `S05_rgb.png` do vùng tối che khuất lòng ghế và bộ SVIRO của Lab 12 không có lớp `occupied = yes` (chỉ có `no` và `unknown`), tôi tạm gán box `child_seat` với `occupied = unknown` trên ảnh RGB (không nhìn chéo sang `S05_ir.png` để điền `no`) theo đúng quy tắc 4.4-1 và 4.8 của Guideline v1.0.

2. Câu hỏi: Với các điểm mốc `face13` vẫn nằm bên trong biên khung hình nhưng bị sống mũi hoặc góc nghiêng đầu che khuất hoàn toàn khi tài xế quay ngang mạnh, ranh giới phân biệt giữa cờ `occluded` và `outside` được quy định cụ thể như thế nào để tránh hiểu nhầm `outside` là nằm ngoài mép ảnh?
   Khung ví dụ: `D01.png` (điểm `mouth_right`) và `D02.png` (điểm `left_eye_outer`)
   Bạn tạm gán thế nào và vì sao: Sau khi đối chiếu chéo theo mục 4.6, tôi tạm bật cờ `occluded` và tắt `outside` cho các điểm này vì điểm mốc vẫn nằm trong vùng khuôn mặt bên trong khung hình và có thể ước lượng tương đối vị trí theo cấu trúc giải phẫu mặt chứ không nằm ngoài biên ảnh.