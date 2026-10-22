Mã dự án: LAB-AGENT

# Báo cáo tuần: Tuần 40 (28/09/2026 - 02/10/2026)

Nguồn: `data/weekly_notes.md`

## Đã hoàn thành
- Endpoint đăng nhập (Lan) (28/09/2026): Hoàn thành endpoint POST /auth/login, đã merge vào nhánh main, có unit test cho đăng nhập đúng và sai mật khẩu.

## Đang thực hiện
- Refresh token (Minh): Đang implement refresh token rotation, xong khoảng 60%. Còn phần thu hồi refresh token cũ khi đăng xuất.

## Vướng mắc
- Lỗi test OAuth (Hoa): Test tích hợp đăng nhập OAuth với Google thất bại trên staging do redirect URI không khớp. Chưa xác định cấu hình nào sai.

## Thông tin cần bổ sung
- Tài liệu API đăng nhập cho mobile: chưa có người phụ trách và chưa có deadline (team mobile cần).
- Lỗi test OAuth: chưa rõ nguyên nhân cụ thể (cấu hình nào không khớp) — Hoa cần xác định.

## Kế hoạch tiếp theo
- Hoàn tất refresh token.
- Tìm nguyên nhân lỗi OAuth trên staging.
- Tài liệu API đăng nhập cho mobile (chưa bắt đầu, chưa có người phụ trách).
- Phân công người viết tài liệu API cho mobile (Cả nhóm, 02/10/2026).
