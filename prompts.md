# Khai báo dùng AI — Trần Đức Hòa

Nhắc lại: không đưa ảnh cabin hay ảnh tài xế (kể cả ảnh chụp màn hình) cho bất kỳ công cụ AI nào.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Gemini | Tra cứu và giải thích các quy tắc trong *Guideline Cabin v1.0* (quy ước ghế theo xe, hướng `facing` của `infant_seat`, nguyên tắc không suy nhãn từ IR sang RGB tối, phân biệt cờ `occluded` và `outside` trên `face13`, các giá trị `gaze_zone`). | Làm cơ sở áp dụng đúng quy tắc khi gán nhãn trên CVAT và trích dẫn điều khoản khi đối chiếu bất đồng với bạn cùng nhóm. | Có. Đối chiếu trực tiếp từng mục với tài liệu *Guideline Cabin v1.0* (Mục 3 & Mục 4), thảo luận thống nhất khi review chéo và kiểm tra bằng `cabin_check.py`. |
| 2 | Gemini | Gỡ lỗi đường dẫn `FileNotFoundError` khi chạy `cabin_check.py` và rà soát cấu trúc các file báo cáo (`disagreement_log.csv`, `ir_log`, `class_list_v0.md`). | Sửa đúng tham số đường dẫn thư mục nhóm trên PowerShell và trình bày đầy đủ chức năng từng lớp nhãn DMS/OMS. | Có. Chạy thực tế lệnh `python scripts/cabin_check.py check` đạt `Kết quả: 0 lỗi` và rà soát thủ công toàn bộ nội dung file trước khi lưu UTF-8. |