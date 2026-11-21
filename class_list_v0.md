# Danh sách lớp v0 — Pham Vu Tung Duong · G05

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | eye_state | open / closed / unknown | Phát hiện buồn ngủ, mắt nhắm lâu, kịp cảnh báo tài xế | Có, trừ khi kính phản xạ hoặc quá tối |
| 2 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Biết tài xế nhìn đâu, phát hiện phân tâm hoặc ngắm không đúng vùng | Có, dựa trên hướng mắt và đầu |
| 3 | glasses | none / clear / sun / unknown | Điều chỉnh độ sáng màn hình và ánh sáng chiếu cho người đeo kính | Có, nhưng kính râm trên NIR có thể trông trong suốt |
| 4 | hand_on_wheel | yes / no / unknown | Phát hiện tay rời vô lăng; trên xe tự lái `no` là bình thường, không phải lỗi | Có, nhìn thấy bàn tay và vị trí |
| 5 | phone_state | held / mounted / lap | Phát hiện dùng điện thoại khi lái, kích hoạt cảnh báo an toàn | Có, chỉ khi thấy rõ hình dạng máy |
| 6 | face_visibility | visible / occluded / not_visible | Biết mặt có bị che hay không, tránh đoán trạng thái tài xế | Có, trừ khi mặt bị che gần hết |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person_in_rear_seat | có / không, theo ghế | Phát hiện người ngồi ghế sau để điều khiển túi khí và báo lỗi | Có, dựa trên hình dạng người |
| 2 | seatbelt_status | worn / not_worn / unknown | Nhắc nhở thắt dây an toàn trước khi xe khởi hành | Có, nhưng tối hoặc bị che thì ghi unknown |
| 3 | child_seat_empty | có / không, theo ghế | Nhắc quên trẻ em trong xe khi ngừng máy | Có, nhận được hình dạng ghế trẻ em trống |
| 4 | object_in_seat | bag / box / cup / other | Phát hiện đồ vật để trên ghế ảnh hưởng việc ngồi hoặc túi khí | Có, dựa trên hình dạng vật |
| 5 | seat_occupancy | occupied / empty | Biết ghế nào có người, ghế nào trống, quản lý ghế | Có, đếm ghế có người vs trống |
| 6 | infant_seat | rear / front, theo ghế | Xác định hướng ghế em bé để bật/tắt túi khí phù hợp | Có, nhận được hình dạng nôi xách |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Trên ảnh D## xoay 90°, khi tài xế nghiêng đầu lateral (xoay cổ về bên vai), quy ước "trái/phải theo người" áp dụng trên trục x hay trục y của ảnh? Mắt trái thực sự nằm ở vị trí nào trên ảnh xoay?
   Khung ví dụ: D04 — tài xế nghiêng đầu về bên trái ảnh, hai mắt gần như nằm trên cùng một hàng ngang.
   Bạn tạm gán thế nào và vì sao: Tôi gán theo trục y (mắt trái có y lớn hơn) vì ảnh xoay ~90°, và ghi chú vào ghi chú của box face để coach xác nhận.

2. Câu hỏi: Trên ảnh IR-sim SVIRO (S##), không có ai thắt dây an toàn, nhưng guideline vẫn cho phép thuộc tính `seatbelt` có giá trị `unknown`. Khi model DMS/OMS sau này được huấn luyện trên dữ liệu này, liệu `unknown` có nên được coi là một lớp riêng hay loại bỏ?
   Khung ví dụ: S07 — ghế rear_right có người, seatbelt ghi `not_worn` (không ai thắt dây trong SVIRO).
   Bạn tạm gán thế nào và vì sao: Tôi ghi `not_worn` vì SVIRO rõ ràng không ai thắt dây, và không ghi `worn_correct/worn_incorrect` theo guideline.
