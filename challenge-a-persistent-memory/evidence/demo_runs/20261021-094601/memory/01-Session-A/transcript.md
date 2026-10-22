User: Quy ước dự án từ nay: mọi báo cáo phải bắt đầu bằng dòng "Mã dự án: LAB-AGENT", mọi ngày viết dạng DD/MM/YYYY.

Tool calls:
- write_file({"path": "output/MEMORY.md", "content": "# Quy ước dự án\n\n## Định dạng báo cáo\n- Mọi bá)
- bash({"command": "ls -la output/ 2>&1; echo \"---\"; cat output/MEMORY.md 2>&1"})

Agent:
Đã lưu quy ước vào `output/MEMORY.md`:

- **Dòng đầu báo cáo:** `Mã dự án: LAB-AGENT`
- **Định dạng ngày:** `DD/MM/YYYY`

Quy ước này sẽ được áp dụng cho mọi báo cáo sau này, kể cả báo cáo tạo bởi skill `csv-quality` và `weekly-report`.
