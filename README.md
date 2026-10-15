# BÀI TẬP LỚN LẬP TRÌNH WEB (PHP 8.x & MySQL)
**Chủ đề lựa chọn:** CHỦ ĐỀ 7: HỆ THỐNG BÁN HÀNG TRỰC TUYẾN MINI  
**Thương hiệu dự kiến:** Tiệm Ăn Vặt & Trà Sữa Bếp Nhà Hà (Bếp Nhà Hà Store)  
**Sinh viên thực hiện:** Bùi Thị Hồng Hà (Làm việc cá nhân độc lập 100%)  
**Mã nguồn:** [https://github.com/BuiThiHongHa/online-shop-mini](https://github.com/BuiThiHongHa/online-shop-mini)

---

## PHIẾU ĐĂNG KÝ ĐỀ TÀI (BIỂU MẪU MỤC 3.1)
- **Học phần:** Lập trình Web (Giảng viên: Trần Thị Thu Phương).
- **Chủ đề:** Chủ đề 7 - Hệ thống bán hàng trực tuyến mini.
- **Người dùng mục tiêu:** Khách hàng (đặt món ăn vặt, trà sữa giao nhanh) và Quản trị viên/Nhân viên (quản lý menu món, kiểm soát tồn kho và duyệt đơn).
- **Phạm vi 8 chức năng cốt lõi:**
  1. CRUD danh mục và món ăn (quản lý tên, giá bán, số lượng tồn kho khả dụng).
  2. Tìm kiếm món ăn và lọc theo danh mục, khoảng giá.
  3. Quản lý giỏ hàng (thêm, sửa số lượng, xóa; chặn thêm vượt tồn kho khả dụng).
  4. Đặt hàng an toàn (server kiểm tra tồn kho, tính lại giá từ CSDL, tự động trừ tồn kho).
  5. Tương tác thời gian thực qua Endpoint JSON & Fetch API kiểm tra tồn kho.
  6. Quản trị đơn hàng và cập nhật trạng thái đơn (Chờ xử lý, Đang làm, Hoàn thành, Hủy).
  7. Xác thực & phân quyền 3 vai trò (Admin, Staff, Customer), mật khẩu băm BCRYPT `password_hash()`, bảo vệ CSRF Token.
  8. Lịch sử mua hàng: Khách hàng theo dõi trạng thái đơn hàng cá nhân.
- **Rủi ro kỹ thuật dự kiến:**
  - Rủi ro bán vượt tồn kho (Overselling): Kiểm tra logic ở CSDL và validate tại server khi checkout.
  - Rủi ro sửa giá từ client: Server tự tính lại tổng tiền dựa trên giá CSDL.

---

## PHÂN TÍCH USER STORIES & 3 VAI TRÒ NGƯỜI DÙNG
- **Khách hàng (Customer - Role 0):**
  - Tìm kiếm và lọc món ăn theo danh mục và khoảng giá.
  - Xem tình trạng tồn kho theo thời gian thực (tránh đặt món đã hết).
  - Thêm món vào giỏ, cập nhật số lượng và đặt hàng.
  - Xem lịch sử các đơn hàng đã đặt của mình.
- **Nhân viên bán hàng (Staff / Mod - Role 2):**
  - Xem danh sách đơn mới đặt.
  - Tiếp nhận và chuyển trạng thái đơn (Đang xử lý ➔ Hoàn thành / Hủy).
- **Quản trị viên (Admin - Role 1):**
  - Toàn quyền CRUD món ăn, danh mục.
  - Quản lý điều chỉnh số lượng tồn kho `total_stock`, khóa bán khi cần.
  - Quản lý tài khoản người dùng và xem thống kê doanh thu.
