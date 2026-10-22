Mã dự án: LAB-AGENT

# Báo cáo tuần: Tuần 40 (28/09/2026 – 02/10/2026)

Nguồn: `data/weekly_notes.md`

Ngày lập báo cáo: 10/21/2026

## Đã hoàn thành
- Endpoint đăng nhập (Lan, 28/09/2026): Hoàn thành endpoint POST /auth/login, đã merge vào nhánh main, có unit test cho đăng nhập đúng và sai mật khẩu.

## Đang thực hiện
- Refresh token (Minh): Đang implement refresh token rotation, tiến độ khoảng 60%. Còn phần thu hồi refresh token cũ khi đăng xuất.

## Vướng mắc
- Lỗi test OAuth (Hoa): Test tích hợp đăng nhập OAuth với Google thất bại trên staging do redirect URI không khớp. Chưa xác định được cấu hình nào sai.

## Thông tin cần bổ sung
- Tài liệu API đăng nhập cho mobile (01/10/2026): chưa có người phụ trách, chưa có deadline — cần trưởng nhóm phân công người nhận việc và ấn định thời hạn.
- Lỗi test OAuth trên staging: chưa rõ nguyên nhân cụ thể (cấu hình nào sai) — cần Hoa xác định và báo lại cấu hình liên quan.

## Kế hoạch tiếp theo
- Hoàn tất refresh token (Minh).
- Tìm nguyên nhân lỗi OAuth trên staging (Hoa).
- Phân công người viết tài liệu API cho mobile (Cả nhóm).
- Tài liệu API đăng nhập cho mobile (chưa bắt đầu, chưa có người phụ trách).
