# Báo cáo: Kỹ năng xử lý sự cố mã nguồn mở & Chiến lược áp dụng Workaround

## 1. Tiêu chí chọn lọc bình luận trên GitHub Issues
Khi một Issue ở trạng thái `OPEN` có nhiều ý kiến trái chiều:
- **Xác thực cộng đồng (Reactions):** Ưu tiên các bình luận có tỷ lệ phản ứng tích cực cao (`:+1:`, `:heart:`, `:tada:`) và không có phản ứng phản đối (`:-1:`).
- **Thẩm quyền kỹ thuật (Role Badges):** Ưu tiên phản hồi từ người có nhãn `Maintainer`, `Collaborator` hoặc `Author`.
- **Minh chứng mã nguồn (Traceability):** Chọn bình luận có đính kèm liên kết tới Pull Request (PR) hoặc commit cụ thể thay vì các lời khuyên cảm tính như "xóa đi cài lại".

## 2. Phân tích chiến lược Workaround
- **Định nghĩa:** Workaround là giải pháp đường vòng, can thiệp tạm thời ở cấp độ dự án hiện tại để vô hiệu hóa ảnh hưởng của lỗi từ thư viện bên thứ ba mà không cần chờ sửa đổi từ phía nhà phát triển gốc.
- **Tính cấp thiết:** 
  - Vòng đời kiểm thử và phát hành phiên bản mới của bên thứ ba không phụ thuộc vào thời hạn (deadline) của dự án cá nhân/doanh nghiệp.
  - Việc thụ động chờ bản cập nhật sẽ gây gián đoạn toàn bộ tiến độ (blocking dependency).

## 3. Quy trình chuẩn khi triển khai Workaround
1. **Cô lập:** Áp dụng giải pháp ở phạm vi hẹp nhất có thể (chỉ giới hạn trong module gọi thư viện đó).
2. **Gắn thẻ chú thích kỹ thuật:**
   ```javascript
   // TODO: WORKAROUND - Tạm thời xử lý lỗi khởi chạy thư viện (GitHub Issue #123)
   // Xóa bỏ đoạn mã này khi thư viện cập nhật lên phiên bản ổn định tiếp theo.
   ```
3. **Theo dõi (Subscribe):** Đăng ký thông báo tại GitHub Issue liên quan để cập nhật ngay khi mã vá chính thức được phát hành.