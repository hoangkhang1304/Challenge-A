User: Tạo báo cáo tuần.

Tool calls:
- read_file({"path": "skills/weekly-report/SKILL.md"})
- bash({"command": "ls -la; echo \"---\"; ls -la data/ 2>/dev/null; echo \"---\"; ls -la output/ )
- read_file({"path": "data/weekly_notes.md"})
- read_file({"path": "skills/weekly-report/references/report-template.md"})
- write_file({"path": "output/weekly-report.md", "content": "Mã dự án: LAB-AGENT\n\n# Báo cáo tuần: Tuầ)

Agent:
Đã tạo báo cáo tuần tại `output/weekly-report.md`.

Tóm tắt:
- **Đã hoàn thành (1):** endpoint đăng nhập POST /auth/login (Lan, 28/09/2026).
- **Đang thực hiện (1):** refresh token rotation ~60% (Minh, 29/09/2026), còn phần thu hồi token cũ.
- **Vướng mắc (1):** lỗi OAuth redirect URI trên staging (Hoa, 30/09/2026), chưa rõ cấu hình sai.
- **Kế hoạch (3):** hoàn tất refresh token, tìm nguyên nhân lỗi OAuth, phân công người viết tài liệu API cho mobile (việc này chưa bắt đầu).
- **Cần bổ sung:** chưa có người phụ trách và deadline cho tài liệu API mobile, nguyên nhân lỗi OAuth chưa rõ, thiếu deadline cho phần refresh token còn lại.

Báo cáo bắt đầu bằng dòng `Mã dự án: LAB-AGENT` và dùng định dạng ngày `DD/MM/YYYY` theo quy ước dự án.
