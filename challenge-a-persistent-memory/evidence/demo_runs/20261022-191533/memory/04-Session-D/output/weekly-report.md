Mã dự án: LAB-MEMORY

# Báo cáo tuần: Tuần 40 (09/28/2026 - 10/02/2026)

Nguồn: `data/weekly_notes.md`

## Đã hoàn thành
- Endpoint đăng nhập: Lan (09/28/2026)

## Đang thực hiện
- Refresh token (Minh): đang implement refresh token rotation, xong khoảng 60%; còn phần thu hồi refresh token cũ khi đăng xuất

## Vướng mắc
- Lỗi test OAuth (Hoa): test tích hợp đăng nhập OAuth với Google thất bại trên staging do redirect URI không khớp; chưa xác định được cấu hình nào sai

## Thông tin cần bổ sung
- Tài liệu API đăng nhập cho mobile: chưa có người phụ trách và chưa có deadline (team mobile đang cần)
- Lỗi test OAuth: chưa rõ nguyên nhân cụ thể (cấu hình nào sai) và chưa rõ deadline xử lý

## Kế hoạch tiếp theo
- Hoàn tất refresh token
- Tìm nguyên nhân lỗi OAuth trên staging
- Phân công người viết tài liệu API đăng nhập và refresh token cho mobile
- Tài liệu API đăng nhập cho mobile (chưa bắt đầu, chưa có người phụ trách và deadline)
