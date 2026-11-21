# Tự đánh giá — Trần Đức Hòa · G12

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| `S02_rgb.png` | `child_seat` | `ok` | Vùng tối che khuất lòng ghế nên giữ `occupied = unknown`, không nhìn chéo sang `S02_ir.png` để đoán | Không cần sửa |
| `S05_ir.png` | `child_seat` | `wrong_class` | Copy shape từ `S05_rgb` sang nhưng quên cập nhật thuộc tính `occupied` từ `unknown` sang `no` dù ảnh IR nhìn rõ lòng ghế trống | Đã sửa |
| `D01.png` | `face13` (`mouth_right`) | `flag` | Gắn nhầm cờ `outside` thay vì `occluded` cho khóe miệng phải bị góc nghiêng che khuất trong khung hình | Đã sửa |
| `D02.png` | `face13` (`left_eye_outer`) | `flag` | Quên bật cờ `occluded` cho khóe ngoài mắt trái khi điểm mốc bị che khuất một phần | Đã sửa |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Sai hoặc thiếu cờ trạng thái điểm mốc trên `face13` (`flag` — nhầm giữa `occluded` và `outside`, hoặc quên bật cờ `occluded` ở các điểm nằm phía khuất mặt).

Vì sao mình mắc: Khi gán nhanh trên ảnh `D##` xoay 90°, mình dễ nhầm ranh giới giữa `occluded` (điểm bị che khuất nhưng vẫn ước lượng chắc chắn vị trí trên khuôn mặt) và `outside` (điểm không đoán được hoặc nằm ngoài biên ảnh), đồng thời chưa có thói quen mở danh sách điểm ở panel *Objects* để soát lại cờ trước khi lưu.

Lần sau tránh bằng cách: Sau khi đặt đủ 13 điểm `face13`, luôn mở rộng cây thuộc tính bên cột *Objects* để kiểm tra riêng các điểm nằm ở nửa mặt nghiêng/bị che và đối chiếu đúng tiêu chí mục 4.6 trước khi bấm `Ctrl+S`.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: Ở dòng `S05_ir.png, child_seat, occupied` (mình để `unknown`, bạn để `no`) và dòng `D01.png, face13, mouth_right.occluded` (mình đánh nhầm thành `outside`). Mình học được hai điểm cốt lõi: thứ nhất, thao tác copy box từ ảnh RGB sang IR giúp tiết kiệm thời gian nhưng bắt buộc phải rà lại toàn bộ thuộc tính `unknown` để cập nhật những chi tiết mà kênh hồng ngoại nhìn rõ; thứ hai, việc phân biệt đúng cờ `occluded` với `outside` giúp giữ lại thông tin cấu trúc giải phẫu của khuôn mặt thay vì loại bỏ điểm mốc đó khỏi dữ liệu huấn luyện.