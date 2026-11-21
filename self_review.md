# Tự đánh giá — Pham Vu Tung Duong · G05

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb | ghế rear_right | ok | Ghế gọi theo xe, trái ảnh = rear_right vì camera nhìn về phía sau. | có |
| S04_ir | ghế rear_right | ok | Đồ vật cup đặt đúng ghế, modality = ir, light = unknown. | có |
| D02.png | mặt tài xế | ok | face13 đủ 13 điểm, mắt trái y lớn hơn mắt phải (ảnh xoay 90°). | có |
| D05.png | tay trái | ok | on_wheel = no vì xe tự lái, tay không trên vô lăng là bình thường. | có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Nhầm trái/phải ghế trên ảnh SVIRO (ghi rear_left cho người bên trái ảnh).

Vì sao mình mắc: Quên rằng camera OMS nhìn về phía sau xe, nên bên trái ảnh là ghế bên phải của xe.

Lần sau tránh bằng cách: Đứng quay lưng về màn hình như camera rồi chỉ tay trước khi ghi `seat`, và đọc lại quy tắc "ghế gọi theo xe" trước mỗi ảnh.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai: Bạn ghi `seatbelt = unknown` trên S06_ir, tôi ghi `not_worn`. Theo guideline SVIRO không ai thắt dây nên `not_worn` là chính xác. Mình học được: không nên để unknown khi ảnh rõ ràng không có dây an toàn.
