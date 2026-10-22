User: Tạo báo cáo tuần.

Tool calls:
- read_file({"path": "skills/weekly-report/SKILL.md"})
- bash({"command": "ls -la; echo \"---\"; ls -la data/ 2>/dev/null; echo \"---\"; ls -la output/ )
- read_file({"path": "data/weekly_notes.md"})
- read_file({"path": "skills/weekly-report/references/report-template.md"})
- read_file({"path": "output/weekly-report.md"})
- write_file({"path": "output/weekly-report.md", "content": "Mã dự án: LAB-MEMORY\n\n# Báo cáo tuần: Tu)

Agent:
Đã tạo báo cáo tuần tại `output/weekly-report.md` (cập nhật file cũ).

Tóm tắt:
- **Tuần 40 (28/09/2026 – 02/10/2026)**, nguồn `data/weekly_notes.md`.
- **1 việc hoàn thành** (endpoint đăng nhập – Lan), **1 đang thực hiện** (refresh token ~60% – Minh), **1 vướng mắc** (lỗi OAuth trên staging – Hoa), **1 việc chưa bắt đầu** (tài liệu API cho mobile – chưa có người phụ trách).
- Thiếu thông tin cần bổ sung: người nhận việc + deadline cho tài liệu mobile, nguyên nhân lỗi OAuth, deadline cho phần refresh token còn lại.

Lưu ý: file cũ dùng `Mã dự án: LAB-AGENT`, tôi đã đổi sang `LAB-MEMORY` theo quy ước dự án trong memory (memory ưu tiên hơn template).
