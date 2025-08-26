# 2. Yêu cầu

## 2.1. Yêu cầu Chức năng (Functional Requirements)

*   **FR1:** Quản trị viên phải có khả năng quản lý sản phẩm (thêm, sửa, xóa) và phân loại chúng theo các danh mục được xác định trước (ví dụ: thương hiệu, dòng sản phẩm).
*   **FR2:** Người dùng phải có khả năng duyệt sản phẩm thông qua các danh mục được sắp xếp trên thanh điều hướng (navigation bar). Khi người dùng nhấp vào một danh mục, hệ thống sẽ chuyển đến trang của danh mục đó, hiển thị danh sách các sản phẩm tương ứng và cung cấp các công cụ lọc sản phẩm.
*   **FR3:** Hệ thống phải cung cấp một thanh tìm kiếm hiệu quả. Khi người dùng tương tác với thanh tìm kiếm, hệ thống phải hiển thị các gợi ý thông minh, bao gồm: các từ khóa được tìm kiếm nhiều nhất, danh sách các thương hiệu nổi bật, và danh sách các sản phẩm người dùng đã xem gần đây.
*   **FR4:** Người dùng phải có khả năng thêm sản phẩm vào giỏ hàng, xem lại giỏ hàng và tiến hành quy trình thanh toán.
*   **FR5:** Hệ thống phải hỗ trợ tính năng **"Guest Checkout"**, cho phép người dùng mua hàng mà không cần tạo tài khoản.
*   **FR6:** Hệ thống phải tích hợp với các cổng thanh toán phổ biến tại Việt Nam, bao gồm COD (Thanh toán khi nhận hàng), ZaloPay, Momo, và VNPAY.
*   **FR7:** Người dùng phải có tùy chọn đăng ký tài khoản mới hoặc đăng nhập bằng tài khoản mạng xã hội (ví dụ: Google, Facebook).
*   **FR8:** Người dùng đã đăng nhập phải có thể truy cập trang cá nhân để xem lại lịch sử các đơn hàng đã đặt.
*   **FR9:** Phải có một Trang Quản trị (Admin Panel) cơ bản cho phép quản trị viên thực hiện các tác vụ quản lý cốt lõi: quản lý sản phẩm, xem đơn hàng và quản lý người dùng.

## 2.2. Yêu cầu Phi chức năng (Non-Functional Requirements)

*   **NFR1:** Thời gian tải trang trung bình cho các trang chính (trang chủ, trang sản phẩm, trang danh mục) phải dưới 2 giây.
*   **NFR2:** Điểm hiệu suất trên Google PageSpeed Insights cho phiên bản di động phải đạt trên 90.
*   **NFR3:** Toàn bộ kiến trúc hệ thống phải tuân thủ nguyên tắc **Serverless-First** trên nền tảng AWS để đảm bảo khả năng mở rộng và tối ưu chi phí.
*   **NFR4:** Giao diện người dùng phải có thiết kế đáp ứng (responsive), đảm bảo trải nghiệm nhất quán và chất lượng trên cả máy tính để bàn và thiết bị di động.
*   **NFR5:** Hệ thống phải tương thích và hoạt động ổn định trên các phiên bản mới nhất của các trình duyệt phổ biến (Chrome, Firefox, Safari, Edge).
*   **NFR6:** Quá trình xác thực và quản lý thông tin người dùng phải được xử lý một cách an toàn thông qua dịch vụ AWS Cognito.

---