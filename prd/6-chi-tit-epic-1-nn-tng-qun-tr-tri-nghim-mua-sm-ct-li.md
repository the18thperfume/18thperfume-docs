# 6. Chi tiết Epic 1: Nền tảng, Quản trị & Trải nghiệm Mua sắm Cốt lõi

**Mục tiêu Epic:** Mục tiêu của Epic này là thiết lập toàn bộ hạ tầng kỹ thuật, xây dựng các chức năng quản trị cốt lõi (quản lý sản phẩm, xem đơn hàng) và cung cấp một luồng mua sắm hoàn chỉnh cho khách (từ duyệt xem, tìm kiếm đến thanh toán). Khi hoàn thành, chúng ta sẽ có một sản phẩm tối thiểu nhưng hoàn chỉnh, có khả năng tạo ra doanh thu.

## Story 1.1: Thiết lập Nền tảng Dự án (Project Foundation)
*   **Là** một nhà phát triển,
*   **Tôi muốn** thiết lập hai repositories riêng biệt cho frontend và backend, cùng với CI/CD pipeline cơ bản cho mỗi repo,
*   **Để** tạo ra nền tảng vững chắc, cho phép phát triển và triển khai độc lập giữa giao diện người dùng và logic nghiệp vụ.

**Tiêu chí Chấp nhận (Acceptance Criteria):**
1.  Một Git repository cho **Frontend** được khởi tạo. CI/CD pipeline được thiết lập để tự động triển khai lên AWS S3/CloudFront khi có thay đổi.
2.  Một Git repository cho **Backend** được khởi tạo. CI/CD pipeline được thiết lập để tự động triển khai các hàm Lambda khi có thay đổi.
3.  Một API endpoint "health check" của backend và một trang "Coming Soon" của frontend có thể được truy cập công khai qua URL của môi trường phát triển.

## Story 1.2: Quản lý Sản phẩm và Biến thể cho Admin
*   **Là** một quản trị viên,
*   **Tôi muốn** có một giao diện chi tiết để thêm và chỉnh sửa sản phẩm cùng các biến thể giá của nó,
*   **Để** tôi có thể quản lý chính xác và đầy đủ thông tin sản phẩm trên trang web.

**Tiêu chí Chấp nhận (Acceptance Criteria):**
1.  Trong trang quản trị, khi thêm/sửa sản phẩm, có một biểu mẫu (form) với các trường sau:
    *   **Tên sản phẩm:** Tự điền (text input).
    *   **Thương hiệu:** Tự điền (text input).
    *   **Giới tính:** Chọn 1 (dropdown: Nam, Nữ, Unisex).
    *   **Phân khúc:** Chọn 1 (dropdown: Designer, Niche).
    *   **Xuất xứ:** Tự điền (text input).
    *   **Nhóm hương:** Tự điền (text input).
    *   **Nồng độ:** Tự điền (text input).
    *   **Năm ra mắt:** Tự điền (number input).
    *   **Mùa:** Chọn nhiều (checkboxes: Xuân, Hè, Thu, Đông).
    *   **Top Notes:** Tự điền, các giá trị cách nhau bằng dấu phẩy.
    *   **Middle Notes:** Tự điền, các giá trị cách nhau bằng dấu phẩy.
    *   **Base Notes:** Tự điền, các giá trị cách nhau bằng dấu phẩy.
2.  Trường **"Thành phần"** của sản phẩm được hệ thống tự động tạo ra bằng cách tổng hợp tất cả các giá trị từ Top, Middle và Base Notes. Trường này không hiển thị trên form.
3.  Trong cùng một biểu mẫu, có một khu vực để quản lý **"Các biến thể"**, nơi admin có thể thêm, sửa, xóa nhiều biến thể cho một sản phẩm. Mỗi biến thể có các trường:
    *   **Tên biến thể:** Tự điền (ví dụ: "Chiết 10ml", "Fullseal 50ml").
    *   **Giá gốc:** Tự điền (số).
    *   **Mức sale:** Tự điền (số, biểu thị %).
    *   **Tồn kho:** Tự điền (số).
4.  Hệ thống phải tự động rút ra thuộc tính **"Dung tích"** (ví dụ: "Chiết", "Fullseal") từ "Tên biến thể" để phục vụ cho việc lọc sản phẩm sau này.
5.  Tất cả thông tin sản phẩm và biến thể được lưu chính xác vào cơ sở dữ liệu.

## Story 1.3: Hiển thị, Duyệt và Lọc sản phẩm
*   **Là** một người dùng,
*   **Tôi muốn** xem sản phẩm trên các trang danh mục với một bộ lọc mạnh mẽ và bố cục hiển thị rõ ràng,
*   **Để** tôi có thể dễ dàng tìm kiếm và khám phá sản phẩm theo đúng nhu-cầu-của-mình.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

**A. Bố cục trang danh mục:**

1. Trang danh mục được chia thành 2 cột: cột bộ lọc bên trái (chiếm khoảng 25% chiều rộng) và cột danh sách sản phẩm bên phải (chiếm khoảng 75%).
2. Khu vực danh sách sản phẩm hiển thị sản phẩm theo dạng lưới (grid), với 3 hàng và 5 sản phẩm mỗi hàng (tổng cộng 15 sản phẩm mỗi trang).
3. Nếu có nhiều hơn 15 sản phẩm phù hợp với tiêu chí, một nút "Xem thêm" sẽ xuất hiện ở cuối danh sách.
4. Khi nhấn nút "Xem thêm", 15 sản phẩm tiếp theo (3 hàng nữa) sẽ được tải và hiển thị nối tiếp vào danh sách hiện tại.

**B. Chức năng của Bộ lọc:**

1. Bộ lọc bên trái cho phép người dùng lọc sản phẩm theo nhiều tiêu chí cùng lúc.
2. Các tiêu chí lọc bao gồm:
    *   **Giới tính:** Checkbox (Nam, Nữ, Unisex).
    *   **Phân khúc:** Checkbox (Niche, Designer).
    *   **Mùa:** Checkbox (Xuân, Hè, Thu, Đông).
    *   **Nhóm hương:** Checkbox (danh sách các nhóm hương như Citrus, Amber, Floral...).
    *   **Nồng độ:** Checkbox (danh sách các nồng độ như Eau de Parfum, Eau de Toilette...).
    *   **Dung tích chung:** Checkbox (danh sách các loại dung tích như Fullseal, Chiết, Gốc, Mini...). Logic lọc dựa trên từ khóa có trong tên biến thể (ví dụ: biến thể "Chiết 10ml" sẽ khớp với bộ lọc "Chiết").
    *   **Khoảng giá:** Một thanh trượt (slider) cho phép chọn khoảng giá tùy ý, VÀ các mốc giá chọn nhanh được định sẵn (0-1tr, 1-3tr, 3-5tr, 5-8tr, 8-10tr, 10-15tr, trên 15tr). Một sản phẩm sẽ được hiển thị nếu bất kỳ biến thể giá nào của nó nằm trong khoảng giá được chọn.
    *   **Thương hiệu:** Checkbox (danh sách khoảng 80 thương hiệu).
    *   **Năm ra mắt:** Thanh trượt hoặc ô nhập liệu để chọn khoảng năm.
    *   **Xuất xứ:** Checkbox (danh sách các quốc gia).
    *   **Lịch sử mua hàng:** Checkbox ("Sản phẩm đã mua", "Sản phẩm chưa mua"). (Lưu ý: tính năng này chỉ hoạt động khi người dùng đã đăng nhập).
Khi người dùng chọn hoặc bỏ chọn một tiêu chí lọc, danh sách sản phẩm bên phải phải được cập nhật ngay lập tức mà không cần tải lại toàn bộ trang.

**C. Hiển thị sản phẩm trong danh sách:**

1. Mỗi sản phẩm trong danh sách hiển thị hình ảnh đại diện, tên sản phẩm, thương hiệu.
2. Giá hiển thị cho sản phẩm là giá của biến thể rẻ nhất.
3. Có các "swatches" (ô chọn nhỏ) cho phép người dùng thấy các biến thể dung tích khác nhau (ví dụ: 10ml, 20ml, 50ml) và khi di chuột qua, giá sẽ được cập nhật tương ứng.

## Story 1.4: Tìm kiếm Sản phẩm Thông minh với Modal Tức thì
*   **Là** một người dùng,
*   **Tôi muốn** có một trải nghiệm tìm kiếm thông minh và tức thì ngay từ header,
*   **Để** tôi có thể tìm thấy sản phẩm một cách nhanh chóng và chính xác.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

**A. Giao diện và Tương tác:**

1. Trên Header của trang web, có một icon hoặc ô tìm kiếm.
2. Khi người dùng nhấp vào, ô tìm kiếm sẽ mở rộng với hiệu ứng mượt mà và một modal tìm kiếm sẽ xuất hiện ngay lập tức (che phủ một phần nội dung trang).
3. Bên trong modal, có các khu vực gợi ý được hiển thị sẵn (trước khi người dùng gõ):
    *   Gợi ý từ khóa (ví dụ: "Nước hoa mùa hè", "Tom Ford").
    *   Các sản phẩm đã xem gần đây.
    *   Các. thương hiệu nổi bật.

**B. Logic Tìm kiếm và Hiển thị Kết quả:**

1. Khi người dùng bắt đầu gõ vào ô tìm kiếm, khu vực gợi ý sẽ được thay thế bằng kết quả tìm kiếm tức thì.
2. Hệ thống sẽ hiển thị tối đa 5 sản phẩm phù hợp nhất.
3. Thứ tự ưu tiên hiển thị kết quả như sau:
   *   **Ưu tiên 1:** Các sản phẩm có tên chứa chính xác cụm từ được tìm kiếm (ví dụ: tìm "Y Eau de Parfum" sẽ ưu tiên "Yves Saint Laurent Y Eau de Parfum").
   *   **Ưu tiên 2:** Sau đó mới đến các sản phẩm có tên chứa một phần của từ khóa tìm kiếm.
4. Mỗi sản phẩm trong kết quả tìm kiếm hiển thị hình ảnh thu nhỏ, tên sản phẩm và thương hiệu.
5. Nhấp vào một sản phẩm trong kết quả sẽ đưa người dùng đến trang chi tiết sản phẩm đó.

## Story 1.5: Quy trình Giỏ hàng và Thanh toán (Guest Checkout)
*   **Là** một khách hàng (không cần đăng nhập),
*   **Tôi muốn** thêm sản phẩm vào giỏ hàng, điền thông tin giao hàng và hoàn tất thanh toán,
*   **Để** tôi có thể mua hàng một cách nhanh chóng và thuận tiện.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Nút "Thêm vào giỏ hàng" trên trang chi tiết sản phẩm hoạt động.
2. Người dùng có thể xem giỏ hàng, thay đổi số lượng hoặc xóa sản phẩm.
3. Trong trang thanh toán, người dùng có thể điền thông tin người nhận và địa chỉ giao hàng.
4. Người dùng có thể chọn một trong các phương thức thanh toán đã định (COD, ZaloPay, Momo, VNPAY).
5. Sau khi đặt hàng thành công, người dùng nhận được một trang xác nhận với mã đơn hàng.
6. Một email xác nhận đơn hàng được tự động gửi đến địa chỉ email của khách hàng.

## Story 1.6: Quản lý Đơn hàng cho Admin
*   **Là** một quản trị viên,
*   **Tôi muốn** xem danh sách tất cả các đơn hàng đã được đặt trên trang web,
*   **Để** tôi có thể xử lý và thực hiện việc giao hàng cho khách.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Trong trang quản trị, có một mục "Quản lý Đơn hàng".
2. Trang này liệt kê tất cả các đơn hàng với các thông tin cơ bản: mã đơn hàng, tên khách hàng, ngày đặt, tổng tiền và trạng thái.
3. Admin có thể nhấp vào một đơn hàng để xem chi tiết thông tin giao hàng và các sản phẩm đã đặt.
