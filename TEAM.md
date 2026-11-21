# TEAM — Ngày 12

Mã bộ ảnh: **G12** · Hình thức: Cá nhân

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Trần Đức Hòa | 2A202603181 | có | Vũ Thị Thu Huyền - 2A202603115 | 19 |


Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- Không có ca bất đồng nào chưa thống nhất sau khi đối chiếu Guideline Cabin v1.0 (đã ghi nhận và báo coach trường hợp ảnh SVIRO có trẻ em ngồi trong `child_seat` theo mục 3).

## Cá nhân

### TranDucHoa-2A202603181
- Phần mình làm (ngoài 22 ảnh của mình, ví dụ ai review ai, ai tổng hợp ca hỏi coach): Chạy tự kiểm `cabin_check` qua các mốc Checkpoint A, Checkpoint B và bản cuối (đạt 0 lỗi); thực hiện `peer diff` và đối chiếu 19 dòng bất đồng trong `disagreement_log.csv` với bạn cùng mã bộ ảnh, sửa lỗi cập nhật bản `export_final_v2.zip`, ghi nhận hiện tượng hồng ngoại vào `ir_log` và viết `class_list_v0.md`.
- Điều mình học được hôm nay: Nắm chắc nguyên tắc gán nhãn độc lập giữa ảnh RGB và IR (không nhìn chéo từ ảnh rõ sang ảnh tối để đoán), quy ước gọi ghế theo xe trên camera OMS nhìn ngược và tọa độ xoay 90° của mắt/điểm mốc `face13` trên DMS, cùng cách phân biệt đúng cờ `occluded` với `outside`.