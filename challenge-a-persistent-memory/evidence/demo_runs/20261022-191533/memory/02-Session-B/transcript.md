User: Tạo báo cáo tuần.

Tool calls:
- read_file({"path": "skills/weekly-report/SKILL.md"})
- bash({"command": "ls -la; echo '---'; ls -la data output 2>/dev/null"})
- read_file({"path": "data/weekly_notes.md"})
- read_file({"path": "skills/weekly-report/references/report-template.md"})
- write_file({"path": "output/weekly-report.md", "content": "Mã dự án: LAB-AGENT\n\n# Báo cáo tuần: Tuầ)

Agent:
Đã tạo báo cáo tuần tại `output/weekly-report.md` (1.225 bytes, trạng thái created).

Tóm tắt:
- **Tuần 40 (28/09/2026 - 02/10/2026)**, nguồn `data/weekly_notes.md`; báo cáo bắt đầu bằng dòng "Mã dự án: LAB-AGENT" và dùng định dạng ngày DD/MM/YYYY theo quy ước đang hiệu lực.
- 1 việc hoàn thành (endpoint đăng nhập - Lan), 1 đang thực hiện 60% (refresh token - Minh), 1 vướng mắc (lỗi OAuth - Hoa), 1 việc chưa bắt đầu nằm trong Kế hoạch tiếp theo (tài liệu API cho mobile).
- Mục "Thông tin cần bổ sung" nêu việc thiếu người phụ trách/deadline và chưa rõ nguyên nhân lỗi OAuth.
