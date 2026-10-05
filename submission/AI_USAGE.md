# Khai báo sử dụng AI

**Công cụ:** Claude Code (Anthropic, model Claude Opus 5.5), dùng trong terminal của repo.

## Phần tôi tự làm

- Fork, cài môi trường (`make setup`, `make smoke`, `make data`, `make data-ai`).
- Tự chạy cả 8 notebook trong VS Code, lưu output và chụp toàn bộ screenshot.
- Đọc, kiểm tra và chỉnh sửa lại phần giải thích để có thể tự trình bày được.
- Chạy `make test` và `make run-all` để kiểm tra tính tái lập.
- Chọn anti-pattern và chỉnh sửa `REFLECTION.md` theo hệ thống của mình.

## Phần AI hỗ trợ

| Việc | Phạm vi |
|---|---|
| Giải thích repo và quy trình nộp | Tóm tắt README, RUBRIC, CHECKPOINTS, SUBMISSION; hướng dẫn từng notebook cần làm gì |
| Soạn phần "Giải thích kết quả" của NB1–NB8 | AI soạn Markdown cell cuối mỗi notebook dựa trên **output thật** đã lưu trong notebook và đối chiếu thêm file trên đĩa (`_delta_log`, metadata Iceberg). Không có số liệu nào được tạo ra ngoài output thực tế |
| Thêm cell kiểm tra Gold ở NB4 | AI viết code cell kiểm tra bổ sung (p50 ≤ p95, `cost_usd > 0`, `error_rate ∈ [0, 1]`, ≥ 7 ngày × 3 model). Đây là kiểm tra **thêm**, không sửa logic gốc và không hạ ngưỡng; tôi tự chạy cell này |
| Giải thích các output dễ gây hiểu nhầm | Ví dụ NB6: "5 files you pay for" gồm 3 orphan + 2 checkpoint trong `_delta_log/`; NB3: commit RESTORE chỉ có 1 action `remove` | |

## Cam kết

- Không sửa assertion, không hạ ngưỡng, không tạo output giả.
- Mọi notebook do tôi tự thực thi; AI chỉ đọc output đã lưu để viết giải thích.
