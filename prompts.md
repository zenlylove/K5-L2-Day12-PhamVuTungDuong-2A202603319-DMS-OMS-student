# Khai báo dùng AI — Pham Vu Tung Duong

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | Kilo (mô hình kilo-auto/free) | Đọc các file tài liệu lab (README, GUIDE, SUBMISSION, RUBRIC, CHECKPOINTS, templates, scripts/cabin_check.py, scripts/cabin_schema.py) và hướng dẫn tạo file annotations.xml theo định dạng CVAT for images 1.1 cho 22 ảnh G05 | Sinh file annotations.xml (export_final.zip), check_cpA/check_cpB/check_final, ir_log.csv, class_list_v0.md, self_review.md, exit_ticket.md, TEAM.md, prompts.md, disagreement_log.csv | Có. Chạy `python scripts/cabin_check.py check export_final.zip --expect 22 --manifest G05/oms/manifest.csv --out check_final.txt` → kết quả 0 lỗi, 0 cảnh báo. Kiểm lại zip chỉ chứa annotations.xml, không có ảnh. |

Lưu ý: Không đưa ảnh cabin hay ảnh tài xế (kể cả chụp màn hình) vào công cụ AI. AI chỉ được dùng để đọc tài liệu văn bản và sinh file label XML dựa trên guideline.
