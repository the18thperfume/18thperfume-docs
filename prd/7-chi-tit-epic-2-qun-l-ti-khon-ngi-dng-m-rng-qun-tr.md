# 7. Chi tiết Epic 2: Quản lý Tài khoản Người dùng & Mở rộng Quản trị

**Mục tiêu Epic:** Xây dựng các tính năng cho phép người dùng đăng ký, đăng nhập và xem lịch sử đơn hàng. Đồng thời, mở rộng Trang Quản trị để admin có thể quản lý người dùng thành viên, hoàn thiện vòng lặp quản lý của hệ thống.

## Story 2.1: Xác thực Người dùng (Đăng ký/Đăng nhập)
*   **Là** một người dùng,
*   **Tôi muốn** có thể đăng ký tài khoản hoặc đăng nhập một cách dễ dàng, bao gồm cả việc sử dụng tài khoản mạng xã hội,
*   **Để** có thể truy cập các tính năng cá nhân hóa và quản lý đơn hàng của mình.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Trên Header có một icon người dùng. Khi chưa đăng nhập, nhấp vào icon này sẽ mở ra một modal/trang đăng nhập.
2. Giao diện đăng nhập cung cấp các tùy chọn: Đăng nhập bằng email và mật khẩu, hoặc đăng nhập qua Google/Facebook.
3. Người dùng có thể đăng ký một tài khoản mới bằng email.
4. Có chức năng "Quên mật khẩu" để người dùng có thể lấy lại mật khẩu qua email.
5. Sau khi đăng nhập thành công, icon trên header thay đổi để thể hiện trạng thái đã đăng nhập và người dùng được chuyển hướng đến trang chủ hoặc trang tài khoản.

## Story 2.2: Trang Cá nhân và Lịch sử Đơn hàng
*   **Là** một người dùng đã đăng nhập,
*   **Tôi muốn** truy cập vào trang cá nhân của mình để xem lại lịch sử các đơn hàng đã đặt,
*   **Để** tôi có thể theo dõi các giao dịch và sản phẩm mình đã mua.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Khi đã đăng nhập, nhấp vào icon người dùng sẽ dẫn đến trang quản lý tài khoản.
2. Trang tài khoản có một mục rõ ràng là "Lịch sử Đơn hàng".
3. Mục này liệt kê tất cả các đơn hàng được thực hiện bởi tài khoản đó, sắp xếp theo thứ tự mới nhất trước.
4. Mỗi đơn hàng trong danh sách hiển thị các thông tin chính: Mã đơn hàng, Ngày đặt, Tổng tiền, Trạng thái đơn hàng.
5. Người dùng có thể nhấp vào một đơn hàng để xem trang chi tiết đơn hàng đó (bao gồm sản phẩm, địa chỉ giao hàng...).

## Story 2.3: Quản lý Thành viên cho Admin
*   **Là** một quản trị viên,
*   **Tôi. muốn** có thể xem và quản lý danh sách những người dùng đã đăng ký tài khoản,
*   **Để** hỗ trợ khách. hàng và quản lý cộng đồng người dùng trên trang web.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Trong Trang Quản trị, có một mục "Quản lý Thành viên".
2. Trang này hiển thị một bảng danh sách tất cả người dùng đã đăng ký với các thông tin: Tên, Email, Ngày đăng ký.
3. Admin có thể tìm kiếm hoặc lọc danh sách người dùng theo tên hoặc email.
4. Admin có thể nhấp vào một người dùng để xem thông tin chi tiết của họ.
