Mã dự án: LAB-AGENT

# Báo cáo tuần: Tuần 40 (28/09/2026 - 02/10/2026)

Nguồn: `data/weekly_notes.md`

## Đã hoàn thành
- Endpoint đăng nhập (Lan, 28/09/2026): Hoàn thành endpoint POST /auth/login, đã merge vào nhánh main, có unit test cho đăng nhập đúng và sai mật khẩu.

## Đang thực hiện
- Refresh token (Minh, 29/09/2026): Đang implement refresh token rotation, xong khoảng 60%. Còn phần thu hồi refresh token cũ khi đăng xuất.

## Vướng mắc
- Lỗi test OAuth (Hoa, 30/09/2026): Test tích hợp đăng nhập OAuth với Google thất bại trên staging do redirect URI không khớp. Chưa xác định cấu hình nào sai.

## Thông tin cần bổ sung
- Tài liệu API đăng nhập cho mobile (01/10/2026): chưa có người nhận việc và chưa có deadline — Team mobile cần tài liệu API đăng nhập và refresh token.
- Lỗi test OAuth (30/09/2026): chưa rõ nguyên nhân cụ thể (chưa xác định cấu hình nào sai) — cần Hoa làm rõ.
- Refresh token rotation (29/09/2026): nguồn chưa ghi deadline cho phần còn lại — cần Minh bổ sung.

## Kế hoạch tiếp theo
- Hoàn tất refresh token (Minh) — kế hoạch ghi ngày 02/10/2026.
- Tìm nguyên nhân lỗi OAuth trên staging (Hoa) — kế hoạch ghi ngày 02/10/2026.
- Phân công người viết tài liệu API cho mobile (Cả nhóm) — kế hoạch ghi ngày 02/10/2026; việc tài liệu API đăng nhập cho mobile hiện chưa bắt đầu.
