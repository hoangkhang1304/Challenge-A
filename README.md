# Challenge A: persistent memory

**Mục tiêu:** agent nhớ được quy ước dự án qua nhiều session, và cập nhật khi quy ước thay đổi.

- Dùng lại agent đã có: copy từ `stage-04-script-skill` của lab Agent Tools & Skills (`read_file`, `write_file`, `bash`, skill `weekly-report`, `csv-quality`). Thư mục này chạy độc lập, không cần stage-04.
- **Chứng minh 1:** session mới vẫn dùng đúng quy ước đã thống nhất.
- **Chứng minh 2:** quy ước đổi thì các session sau dùng quy ước mới.

## Cơ chế memory

```
Session A: "Quy ước dự án từ nay: ..."  ──write_file──▶  workspace/output/MEMORY.md
                                                              │
Session mới (lịch sử rỗng) ── build_agent() đọc MEMORY.md ◀───┘
                              └─▶ system prompt có khối <memory>…</memory> ─▶ agent áp dụng ngay
Quy ước đổi ──write_file ghi đè TOÀN BỘ MEMORY.md──▶ session sau đọc bản mới
```

- `MEMORY.md` có 2 mục. **Đang hiệu lực**: quy ước được áp dụng, kèm ngày và nguồn. **Đã thay thế**: quy ước cũ, ghi rõ bị thay bằng gì, ngày nào, nguồn nào. Agent chỉ áp dụng mục đầu. Làm vậy theo slide 12 "Memory sai và lỗi thời": đánh dấu quy ước bị thay thế thay vì xóa mất dấu vết.

- Session = một conversation (nút **Session mới** xóa lịch sử). Thứ duy nhất đi qua các session là `MEMORY.md`.
- Agent được build lại ở mỗi lượt, nên `system_prompt()` đọc lại `MEMORY.md` mỗi lượt: quy ước mới có hiệu lực ngay.
- `MEMORY.md` nằm dưới `output/` vì `write_file` chỉ được ghi ở đó; không phải nới quyền tool.

## Thay đổi so với stage 04

| File | Thay đổi |
|---|---|
| `prompts.py` | `MEMORY_PROMPT`: luật dùng và cập nhật memory, mẫu 2 mục Đang hiệu lực / Đã thay thế; `build_system_prompt(..., memory)` thêm ngày hôm nay và khối `<memory>` |
| `agent.py` | `load_memory()`; `system_prompt(memory=True)`, `build_agent(model, memory=True)` (`memory=False` = agent gốc, làm baseline). `GeminiChatOpenAI`: adapter cho endpoint Gemini (bắt buộc `thought_signature`), chỉ bật khi `OPENAI_BASE_URL` là Gemini |
| `paths.py` | `MEMORY_FILE = "output/MEMORY.md"` |
| `app.py`, `config.py`, `.streamlit/config.toml` | Tiêu đề, mục tiêu đề bài, nhãn **Session #n**, nút **Session mới**, panel **Memory dự án**, hướng dẫn kịch bản |
| `demo_memory.py` | Demo tự động 4 session, in khối memory đã inject ở mỗi session, chấm PASS/FAIL (CM1, memory đánh dấu quy ước cũ, CM2), lưu bằng chứng |
| `tests/` | Test memory vào prompt của session mới (mock model), test hàm chấm; cập nhật tiêu đề và danh sách module |

## Chạy

Trong thư mục `challenge-a-persistent-memory`:

```bash
uv sync --locked
cp -n .env.example .env   # điền OPENAI_API_KEY, MODEL_NAME, OPENAI_BASE_URL
```

**Giao diện (demo bằng tay):** `uv run streamlit run app.py`, mở http://localhost:8501, làm theo hướng dẫn hiện trong khung chat. Panel **Memory dự án** bên phải hiện nội dung `MEMORY.md` sau mỗi lượt.

**Demo tự động:**

```bash
uv run python demo_memory.py            # có memory: A dạy quy ước, B báo cáo (CM1), C đổi quy ước (kiểm memory), D báo cáo (CM2)
uv run python demo_memory.py baseline   # cùng kịch bản với agent gốc (không memory)
uv run python demo_memory.py all        # cả hai + bảng so sánh
```

Mỗi lần chạy xóa `workspace/output/` (bản cũ được lưu vào bằng chứng). Trước session tạo báo cáo, report cũ bị xóa, `MEMORY.md` giữ nguyên, để kết quả chỉ phụ thuộc memory. Bằng chứng: `evidence/demo_runs/<thời gian>/<chế độ>/<session>/` gồm `system_prompt.md`, `transcript.md`, `output/`, và `summary.md`.

**Test** (không cần API key): `uv run python -m pytest -q`. Test `test_bash`, `test_files` (symlink), `test_check_csv` cần POSIX/WSL như stage 04, lỗi trên Windows.

## Bằng chứng đã có (`evidence/`)

| Thư mục | Nội dung |
|---|---|
| `baseline-ui-traces/` | Trace chạy bằng tay trên UI **trước khi có memory** (agent gốc): model tự ghi `project-conventions.md`, session sau chỉ tìm thấy nhờ `ls output/` (đến 11 tool call); khi quy ước đổi sang MM/DD, report áp dụng không nhất quán (1 ngày đúng, 4 ngày sai). `debug.log` + trace `091824`: lỗi `thought_signature` của Gemini trước khi có adapter |
| `demo_runs/20261021-094601/` | Lần chạy cũ (prompt cũ: xóa quy ước cũ), model `minimax/minimax-m3.1-flash:free`: **CM1 PASS**; CM2: `MEMORY.md` được ghi đè đúng, mã dự án đổi đúng nhưng ngày vẫn DD/MM vì model chép từ report cũ (chạy trước khi demo xóa report cũ) |
| `demo_runs/20261022-191533/` | **Lần chạy mới nhất, code hiện tại: CM1 PASS, memory đánh dấu quy ước cũ PASS, CM2 PASS.** Session C ghi `LAB-AGENT`, `DD/MM/YYYY` xuống mục "Đã thay thế" kèm ngày và nguồn; Session D (lịch sử rỗng, report cũ đã xóa) tạo report `LAB-MEMORY`, ngày MM/DD. `system_prompt.md` mỗi session là phần memory đã inject |
| `output-cuoi-lan-chay-truoc/` | `MEMORY.md` và report cuối của lần chạy `20261022-191533` |
