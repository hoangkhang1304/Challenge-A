User: Quy ước dự án thay đổi: mã dự án đổi thành LAB-MEMORY, mọi ngày viết dạng MM/DD/YYYY.

Tool calls:
- read_file({"path": "output/MEMORY.md"})
- bash({"command": "ls -la output/ 2>/dev/null; echo \"---\"; ls -R . --ignore=.git | head -50"})
- write_file({"path": "output/MEMORY.md", "content": "# Quy ước dự án\n## Đang hiệu lực\n- Mọi báo cáo )
- read_file({"path": "output/weekly-report.md"})
- read_file({"path": "skills/weekly-report/SKILL.md"})
- read_file({"path": "data/weekly_notes.md"})
- read_file({"path": "skills/weekly-report/references/report-template.md"})
- write_file({"path": "output/MEMORY.md", "content": "# Quy ước dự án\n## Đang hiệu lực\n- Mọi báo cáo )
- write_file({"path": "output/weekly-report.md", "content": "Mã dự án: LAB-MEMORY\n\n# Báo cáo tuần: Tu)

Agent:
Đã cập nhật theo quy ước mới.

**Memory** (`output/MEMORY.md`):
- Đang hiệu lực: mã dự án `LAB-MEMORY`, ngày theo `MM/DD/YYYY`
- Đã thay thế: `LAB-AGENT` → `LAB-MEMORY`; `DD/MM/YYYY` → `MM/DD/YYYY` (ngày 10/22/2026)

**Báo cáo cũ** (`output/weekly-report.md`) — đã tạo lại từ nguồn `data/weekly_notes.md` theo quy ước mới:
- Dòng đầu: `Mã dự án: LAB-MEMORY`
- Tuần 40: `09/28/2026 - 10/02/2026`
- Các mốc ngày trong nội dung cũng chuyển sang `09/28/2026`, `10/02/2026`

Lưu ý: file CSV `data/tasks.csv` vẫn giữ nguyên, chưa định dạng lại vì chưa có yêu cầu kiểm tra chất lượng.
