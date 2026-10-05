# Thông tin bài nộp

| Mục | Giá trị |
|---|---|
| Họ tên | Lê Tuấn Anh |
| MSSV | 2A202602952 |
| Mã bài | K4-Track02-Day18 — Data Lakehouse Architecture |
| Đường chạy | Lightweight (`deltalake` + `pyiceberg` + DuckDB + Polars) cho cả 8 notebook; không dùng Spark |
| Python | 3.12.13 (kernel `.venv`) |
| Hệ điều hành | macOS 26.4.1 (Apple silicon) |
| Editor | VS Code (Jupyter extension) |

## Phiên bản thư viện chính

| Thư viện | Phiên bản |
|---|---|
| deltalake | 1.6.6 |
| pyiceberg | 0.12.0 |
| duckdb | 1.5.6 |
| polars | 1.44.2 |
| pyarrow | 25.0.1 |

## Kiểm tra tái lập (Part C)

| Lệnh | Kết quả | Ảnh |
|---|---|---|
| `make test` | 24/24 test pass (100%) | `screenshots/partC_make_test.png` |
| `make run-all` | 8/8 notebook pass trong 14,6 s | `screenshots/partC_run_all.png` |

## Nội dung bài nộp

- `notebooks/` — 8 notebook đã thực thi, giữ output; mỗi notebook có một Markdown cell "Giải thích kết quả" ở cuối.
  NB4 có thêm một code cell kiểm tra Gold (p50 ≤ p95, `cost_usd > 0`, `error_rate ∈ [0, 1]`) vì notebook gốc chưa assert các điều kiện này.
- `screenshots/` — ảnh bằng chứng, đặt tên theo `nbXX_<nội dung>.png`.
- `REFLECTION.md` — reflection ≤ 200 từ.
- `AI_USAGE.md` — khai báo phạm vi sử dụng AI.
