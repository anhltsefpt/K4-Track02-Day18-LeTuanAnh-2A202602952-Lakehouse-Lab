# Reflection — Small-file problem

**Anti-pattern chọn:** ingest streaming tạo hàng loạt file nhỏ mà không có job maintenance định kỳ.

**Vì sao hệ thống của tôi dễ gặp:** hệ thống log gọi LLM ghi
micro-batch vài giây một lần, mỗi commit đều đúng nhưng số file tăng liên tục. NB6 tái hiện: 200 commit tạo 200 file
trung bình 51,5 KB, log 200 JSON. Point query phải mở 11/11 file vì min/max chồng lấn; ở quy mô thật, chi phí GET và
metadata tăng theo số file, không theo dung lượng (managed compaction: 24% hóa đơn đến từ số object).

**Phòng tránh:**
1. Tăng trigger interval hoặc gom batch ở writer để file ra đời đã đủ lớn.
2. Lên lịch compaction + Z-order theo cột lọc chính: NB6 giảm 200 → 11 file (18×), point query chỉ mở 1/10 file.
3. Chạy expiry **kèm** orphan sweep, retention ≥ 7 ngày; NB6 cho thấy expiry Iceberg không xóa file nào nếu đứng một mình.
4. Checkpoint log định kỳ và giám sát số file/partition như một metric có ngưỡng cảnh báo.


