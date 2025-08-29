# Tài liệu Yêu cầu Sản phẩm (PRD) cho 18thPerfume

## 1. Mục tiêu và Bối cảnh

### 1.1. Mục tiêu

Dưới đây là các mục tiêu chính mà sản phẩm này hướng tới, dựa trên bản tóm tắt dự án:

*   **Mục tiêu kinh doanh:**
    *   Ra mắt thành công MVP (Sản phẩm Khả thi Tối thiểu) với các tính năng cốt lõi để nhanh chóng tiếp cận thị trường.
    *   Tối ưu hóa tỷ lệ chuyển đổi bằng cách loại bỏ các rào cản trong trải nghiệm người dùng, đặc biệt là ở quy trình thanh toán.
    *   Giữ chi phí vận hành ở mức tối thiểu bằng cách tận dụng kiến trúc serverless.
*   **Mục tiêu người dùng:**
    *   Cho phép người dùng hoàn thành một giao dịch mua hàng trong dưới 2 phút.
    *   Đảm bảo người dùng có thể dễ dàng tìm thấy sản phẩm họ muốn.
    *   Xây dựng sự tin tưởng và cảm giác an toàn cho người dùng khi thực hiện giao dịch.

### 1.2. Bối cảnh

Dự án này tập trung vào việc xây dựng một trang web e-commerce chuyên biệt cho mặt hàng nước hoa tại thị trường Việt Nam. Nền tảng được thiết kế để giải quyết các vấn đề phổ biến mà người dùng đang gặp phải, bao gồm hiệu suất trang web kém, tốc độ tải chậm và quy trình thanh toán phức tạp thường yêu cầu đăng ký bắt buộc.

Bằng cách áp dụng kiến trúc Serverless-First trên AWS, giải pháp của chúng tôi hướng đến việc cung cấp một trải nghiệm mua sắm vượt trội: nhanh chóng, đáng tin cậy và liền mạch. Điều này không chỉ giúp giải quyết các điểm đau của người dùng mà còn tạo ra một nền tảng vững chắc, có khả năng mở rộng linh hoạt và tối ưu về chi phí vận hành, phục vụ cả những người mới tìm hiểu về nước hoa lẫn những khách hàng sành sỏi.

### 1.3. Lịch sử Thay đổi

| Ngày | Phiên bản | Mô tả | Tác giả |
| :--- | :--- | :--- | :--- |
| 26/08/2025 | 1.0 | Tạo tài liệu ban đầu từ Project Brief. | John (PM) |

---

## 2. Yêu cầu

### 2.1. Yêu cầu Chức năng (Functional Requirements)

*   **FR1:** Quản trị viên phải có khả năng quản lý sản phẩm (thêm, sửa, xóa) và phân loại chúng theo các danh mục được xác định trước (ví dụ: thương hiệu, dòng sản phẩm).
*   **FR2:** Người dùng phải có khả năng duyệt sản phẩm thông qua các danh mục được sắp xếp trên thanh điều hướng (navigation bar). Khi người dùng nhấp vào một danh mục, hệ thống sẽ chuyển đến trang của danh mục đó, hiển thị danh sách các sản phẩm tương ứng và cung cấp các công cụ lọc sản phẩm.
*   **FR3:** Hệ thống phải cung cấp một thanh tìm kiếm hiệu quả. Khi người dùng tương tác với thanh tìm kiếm, hệ thống phải hiển thị các gợi ý thông minh, bao gồm: các từ khóa được tìm kiếm nhiều nhất, danh sách các thương hiệu nổi bật, và danh sách các sản phẩm người dùng đã xem gần đây.
*   **FR4:** Người dùng phải có khả năng thêm sản phẩm vào giỏ hàng, xem lại giỏ hàng và tiến hành quy trình thanh toán.
*   **FR5:** Hệ thống phải hỗ trợ tính năng **"Guest Checkout"**, cho phép người dùng mua hàng mà không cần tạo tài khoản.
*   **FR6:** Hệ thống phải hỗ trợ phương thức thanh toán khi nhận hàng (COD).
*   **FR7:** Người dùng phải có tùy chọn đăng ký tài khoản mới hoặc đăng nhập bằng tài khoản mạng xã hội (ví dụ: Google, Facebook).
*   **FR8:** Người dùng đã đăng nhập phải có thể truy cập trang cá nhân để xem lại lịch sử các đơn hàng đã đặt.
*   **FR9:** Phải có một Trang Quản trị (Admin Panel) cơ bản cho phép quản trị viên thực hiện các tác vụ quản lý cốt lõi: quản lý sản phẩm, xem đơn hàng và quản lý người dùng.

### 2.2. Yêu cầu Phi chức năng (Non-Functional Requirements)

*   **NFR1:** Thời gian tải trang trung bình cho các trang chính (trang chủ, trang sản phẩm, trang danh mục) phải dưới 2 giây.
*   **NFR2:** Điểm hiệu suất trên Google PageSpeed Insights cho phiên bản di động phải đạt trên 90.
*   **NFR3:** Toàn bộ kiến trúc hệ thống phải tuân thủ nguyên tắc **Serverless-First** trên nền tảng AWS để đảm bảo khả năng mở rộng và tối ưu chi phí.
*   **NFR4:** Giao diện người dùng phải có thiết kế đáp ứng (responsive), đảm bảo trải nghiệm nhất quán và chất lượng trên cả máy tính để bàn và thiết bị di động.
*   **NFR5:** Hệ thống phải tương thích và hoạt động ổn định trên các phiên bản mới nhất của các trình duyệt phổ biến (Chrome, Firefox, Safari, Edge).
*   **NFR6:** Quá trình xác thực và quản lý thông tin người dùng phải được xử lý một cách an toàn thông qua dịch vụ AWS Cognito.

---
## 3. Mục tiêu Thiết kế Giao diện Người dùng

### 3.1. Tầm nhìn Tổng thể về UX (Overall UX Vision)

Tầm nhìn là tạo ra một trải nghiệm mua sắm nước hoa trực tuyến **sang trọng, nhanh chóng và đáng tin cậy**. Giao diện phải sạch sẽ, tập trung vào hình ảnh sản phẩm chất lượng cao và cung cấp một luồng thao tác mượt mà, từ khám phá sản phẩm đến thanh toán, giảm thiểu tối đa các bước không cần thiết.

### 3.2. Các Mô hình Tương tác Chính (Key Interaction Paradigms)

*   **Khám phá dựa trên danh mục:** Người dùng dễ dàng duyệt sản phẩm qua các danh mục rõ ràng trên thanh điều hướng.
*   **Tìm kiếm thông minh:** Thanh tìm kiếm là trung tâm, cung cấp gợi ý tức thì và kết quả chính xác.
*   **Thanh toán không gián đoạn:** Quy trình thanh toán "Guest Checkout" là luồng chính, loại bỏ mọi rào cản đăng ký.

### 3.3. Các Màn hình và Chế độ xem Cốt lõi (Core Screens and Views)

Đây là các màn hình quan trọng nhất để hiện thực hóa giá trị của sản phẩm:

*   Trang chủ (Homepage)
*   Trang danh sách sản phẩm (Category/Listing Page)
*   Trang chi tiết sản phẩm (Product Detail Page)
*   Trang Giỏ hàng & Thanh toán (Shopping Cart & Checkout Page)
*   Trang quản lý tài khoản người dùng (bao gồm lịch sử đơn hàng)
*   Trang quản trị (Admin Panel)

### 3.4. Hỗ trợ Tiếp cận (Accessibility)

*   **Mức độ:** WCAG AA. Chúng ta cần đảm bảo trang web có thể được sử dụng bởi càng nhiều người dùng càng tốt, bao gồm cả những người có khuyết tật.

### 3.5. Nhận diện Thương hiệu (Branding)

*   Giao diện cần tuân thủ theo bộ nhận diện thương hiệu của 18thPerfume (nếu có). Tạm thời, chúng ta sẽ hướng đến một phong cách thiết kế tối giản, hiện đại và thanh lịch, sử dụng tông màu trung tính để làm nổi bật sản phẩm.

### 3.6. Nền tảng và Thiết bị Mục tiêu

*   **Nền tảng:** Web Responsive. Giao diện phải hoạt động hoàn hảo trên cả máy tính để bàn và các thiết bị di động (điện thoại, máy tính bảng).

---

## 4. Các giả định về Kỹ thuật

### 4.1. Cấu trúc Repository

*   **Lựa chọn:** Polyrepo (Multi-repo)
*   **Lý do:** Để quản lý và triển khai độc lập giữa hai phần chính của ứng dụng: Frontend (giao diện người dùng, triển khai trên S3/CloudFront) và Backend (logic nghiệp vụ, triển khai trên AWS Lambda). Cách tiếp cận này giúp hai đội (hoặc hai luồng công việc) có thể phát triển song song mà không ảnh hưởng lẫn nhau.

### 4.2. Kiến trúc Dịch vụ

*   **Lựa chọn:** Dựa trên kiến trúc Serverless-First của AWS.
*   **Lý do:** Để tận dụng tối đa khả năng mở rộng tự động, tính sẵn sàng cao và chi phí tối ưu của các dịch vụ serverless như AWS Lambda, API Gateway, và DynamoDB.

---

## 5. Danh sách Epic (Epic List)

*   **Epic 1: Nền tảng, Quản trị & Trải nghiệm Mua sắm Cốt lõi (Foundation, Admin & Core Shopping Experience)**
    *   **Mục tiêu:** Thiết lập hạ tầng kỹ thuật, xây dựng các **chức năng quản trị cốt lõi (quản lý sản phẩm, xem đơn hàng)** và cung cấp một luồng mua sắm hoàn chỉnh cho khách (từ duyệt xem, tìm kiếm đến thanh toán). Epic này tạo ra một vòng lặp giá trị hoàn chỉnh đầu tiên: admin có thể thêm sản phẩm, và khách hàng có thể mua được hàng.

*   **Epic 2: Quản lý Tài khoản Người dùng & Mở rộng Quản trị (User Account & Admin Expansion)**
    *   **Mục tiêu:** Xây dựng các tính năng cho phép người dùng đăng ký/đăng nhập và xem lịch sử đơn hàng. Đồng thời, mở rộng Trang Quản trị để admin có thể **quản lý người dùng thành viên**.

---

## 6. Chi tiết Epic 1: Nền tảng, Quản trị & Trải nghiệm Mua sắm Cốt lõi

**Mục tiêu Epic:** Mục tiêu của Epic này là thiết lập toàn bộ hạ tầng kỹ thuật, xây dựng các chức năng quản trị cốt lõi (quản lý sản phẩm, xem đơn hàng) và cung cấp một luồng mua sắm hoàn chỉnh cho khách (từ duyệt xem, tìm kiếm đến thanh toán). Khi hoàn thành, chúng ta sẽ có một sản phẩm tối thiểu nhưng hoàn chỉnh, có khả năng tạo ra doanh thu.

### Story 1.1: Thiết lập Nền tảng Dự án (Project Foundation)
*   **Là** một nhà phát triển,
*   **Tôi muốn** thiết lập hai repositories riêng biệt cho frontend và backend, cùng với CI/CD pipeline cơ bản cho mỗi repo,
*   **Để** tạo ra nền tảng vững chắc, cho phép phát triển và triển khai độc lập giữa giao diện người dùng và logic nghiệp vụ.

**Tiêu chí Chấp nhận (Acceptance Criteria):**
1.  Một Git repository cho **Frontend** được khởi tạo. CI/CD pipeline được thiết lập để tự động triển khai lên AWS S3/CloudFront khi có thay đổi.
2.  Một Git repository cho **Backend** được khởi tạo. CI/CD pipeline được thiết lập để tự động triển khai các hàm Lambda khi có thay đổi.
3.  Một API endpoint "health check" của backend và một trang "Coming Soon" của frontend có thể được truy cập công khai qua URL của môi trường phát triển.

### Story 1.2: Quản lý Sản phẩm và Biến thể cho Admin
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
4.  Hệ thống phải tự động rút ra thuộc tính **"Dung tích"** (ví dụ: "Chiết", "Fullseal") từ "Tên biến thể" để phục vụ cho việc lọc sản phẩm sau này.
5.  Tất cả thông tin sản phẩm và biến thể được lưu chính xác vào cơ sở dữ liệu.

### Story 1.3: Hiển thị, Duyệt và Lọc sản phẩm
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
3. Có các "swatches" (ô chọn nhỏ) cho phép người dùng thấy các biến thể dung tích khác nhau (ví dụ: 10ml, 20ml, 50ml) và khi di chuột qua rồi click vào, giá sẽ được cập nhật tương ứng.

### Story 1.4: Tìm kiếm Sản phẩm Thông minh với Modal Tức thì
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

### Story 1.5: Quy trình Giỏ hàng và Thanh toán Hợp nhất
*   **Là** một khách hàng,
*   **Tôi muốn** xem lại giỏ hàng và hoàn tất việc đặt hàng trên cùng một trang,
*   **Để** có một trải nghiệm mua sắm liền mạch và nhanh chóng.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1.  Khi người dùng nhấn nút "Thêm vào giỏ hàng", một thông báo (notification) sẽ hiển thị xác nhận sản phẩm đã được thêm.
2.  Thông báo này phải chứa: ảnh thumbnail của sản phẩm, tên sản phẩm, số lượng, và một nút "Xem giỏ hàng".
3.  Người dùng được chuyển đến trang "Giỏ hàng & Thanh toán" khi nhấp vào icon giỏ hàng trên header hoặc nút "Xem giỏ hàng" trong thông báo.
4.  Trên trang "Giỏ hàng & Thanh toán", người dùng có thể xem lại danh sách sản phẩm (bao gồm thông tin biến thể đã chọn), thay đổi số lượng, hoặc xóa sản phẩm khỏi giỏ hàng.
5.  Phương thức thanh toán duy nhất là "Thanh toán khi nhận hàng" (COD) và được chọn mặc định.
6.  **Đối với khách vãng lai (chưa đăng nhập):**
    *   Phải điền đầy đủ các thông tin giao hàng bắt buộc: Họ và tên, Số điện thoại, Email, Địa chỉ.
7.  **Đối với thành viên (đã đăng nhập):**
    *   Các trường thông tin Họ và tên, Số điện thoại, Email được tự động điền từ thông tin tài khoản.
    *   Người dùng có thể chỉnh sửa thông tin giao hàng nếu cần.
8.  Sau khi nhấn nút "Hoàn tất đơn hàng", hệ thống sẽ tạo đơn hàng thành công.
9.  Một email xác nhận đơn hàng được tự động gửi đến địa chỉ email của khách hàng.
10. Đồng thời, một email thông báo có đơn hàng mới được gửi đến email của quản trị viên.

### Story 1.6: Quản lý Đơn hàng cho Admin
*   **Là** một quản trị viên,
*   **Tôi muốn** xem danh sách tất cả các đơn hàng đã được đặt trên trang web,
*   **Để** tôi có thể xử lý và thực hiện việc giao hàng cho khách.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Trong trang quản trị, có một mục "Quản lý Đơn hàng".
2. Trang này liệt kê tất cả các đơn hàng với các thông tin cơ bản: mã đơn hàng, tên khách hàng, ngày đặt, tổng tiền và trạng thái.
3. Admin có thể nhấp vào một đơn hàng để xem chi tiết thông tin giao hàng và các sản phẩm đã đặt.

## 7. Chi tiết Epic 2: Quản lý Tài khoản Người dùng & Mở rộng Quản trị

**Mục tiêu Epic:** Xây dựng các tính năng cho phép người dùng đăng ký, đăng nhập và xem lịch sử đơn hàng. Đồng thời, mở rộng Trang Quản trị để admin có thể quản lý người dùng thành viên, hoàn thiện vòng lặp quản lý của hệ thống.

### Story 2.1: Xác thực Người dùng (Đăng ký/Đăng nhập)
*   **Là** một người dùng,
*   **Tôi muốn** có thể đăng ký tài khoản hoặc đăng nhập một cách dễ dàng, bao gồm cả việc sử dụng tài khoản mạng xã hội,
*   **Để** có thể truy cập các tính năng cá nhân hóa và quản lý đơn hàng của mình.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Trên Header có một icon người dùng. Khi chưa đăng nhập, nhấp vào icon này sẽ mở ra một modal/trang đăng nhập.
2. Giao diện đăng nhập cung cấp các tùy chọn: Đăng nhập bằng email và mật khẩu, hoặc đăng nhập qua Google/Facebook/Zalo.
3. Người dùng có thể đăng ký một tài khoản mới bằng email và có gửi mail xác thực để kích hoạt tài khoản.
4. Có chức năng "Quên mật khẩu" để người dùng có thể lấy lại mật khẩu qua email.
5. Sau khi đăng nhập thành công, icon trên header thay đổi để thể hiện trạng thái đã đăng nhập và người dùng được chuyển hướng đến trang chủ hoặc trang tài khoản.

### Story 2.2: Trang Cá nhân và Lịch sử Đơn hàng
*   **Là** một người dùng đã đăng nhập,
*   **Tôi muốn** truy cập vào trang cá nhân của mình để xem lại lịch sử các đơn hàng đã đặt,
*   **Để** tôi có thể theo dõi các giao dịch và sản phẩm mình đã mua.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Khi đã đăng nhập, nhấp vào icon người dùng sẽ dẫn đến trang quản lý tài khoản.
2. Trang tài khoản có một mục rõ ràng là "Lịch sử Đơn hàng".
3. Mục này liệt kê tất cả các đơn hàng được thực hiện bởi tài khoản đó, sắp xếp theo thứ tự mới nhất trước.
4. Mỗi đơn hàng trong danh sách hiển thị các thông tin chính: Mã đơn hàng, Ngày đặt, Tổng tiền, Trạng thái đơn hàng.
5. Người dùng có thể nhấp vào một đơn hàng để xem trang chi tiết đơn hàng đó (bao gồm sản phẩm, địa chỉ giao hàng...).

### Story 2.3: Quản lý Thành viên cho Admin
*   **Là** một quản trị viên,
*   **Tôi. muốn** có thể xem và quản lý danh sách những người dùng đã đăng ký tài khoản,
*   **Để** hỗ trợ khách. hàng và quản lý cộng đồng người dùng trên trang web.

**Tiêu chí Chấp nhận (Acceptance Criteria):**

1. Trong Trang Quản trị, có một mục "Quản lý Thành viên".
2. Trang này hiển thị một bảng danh sách tất cả người dùng đã đăng ký với các thông tin: Tên, Email, Ngày đăng ký.
3. Admin có thể tìm kiếm hoặc lọc danh sách người dùng theo tên hoặc email.
4. Admin có thể nhấp vào một người dùng để xem thông tin chi tiết của họ.

# Next Steps

## UX Expert Prompt
Chào UX-Agent,

Dưới đây là Tài liệu Yêu cầu Sản phẩm (PRD) chi tiết cho dự án website e-commerce 18thPerfume. Tài liệu này bao gồm các mục tiêu, yêu cầu chức năng, mục tiêu thiết kế, và các user story cụ thể.

Nhiệm vụ của bạn là:
1.  **Nghiên cứu tài liệu PRD đính kèm.**
2.  **Tạo ra các wireframe hoặc mockups chi tiết** cho các màn hình cốt lõi đã được định nghĩa trong phần "Mục tiêu Thiết kế Giao diện Người dùng" (mục 3.3).
3.  **Thiết kế một luồng người dùng (user flow)** mượt mà và logic cho các kịch bản chính: khám phá sản phẩm, tìm kiếm, và quy trình thanh toán "Guest Checkout".
4.  Đảm bảo các thiết kế tuân thủ các mục tiêu về UX/UI và hỗ trợ tiếp cận (WCAG AA) đã nêu trong PRD.

Vui lòng tập trung vào việc tạo ra một thiết kế sang trọng, hiện đại và dễ sử dụng.

## Architect Prompt
Chào Architect-Agent,

Dưới đây là Tài liệu Yêu cầu Sản phẩm (PRD) hoàn chỉnh cho dự án website e-commerce 18thPerfume. Tài liệu này đã xác định rõ các yêu cầu chức năng, phi chức năng, các giả định kỹ thuật, và đã được bẻ nhỏ thành các Epic và User Story.

Nhiệm vụ của bạn là:
1.  **Nghiên cứu kỹ lưỡng tài liệu PRD đính kèm.**
2.  **Thiết kế một bản kiến trúc kỹ thuật chi tiết** cho toàn bộ hệ thống, tuân thủ nghiêm ngặt các giả định đã được phê duyệt (Polyrepo, Serverless-First trên AWS, DynamoDB, Lambda, S3, CloudFront, Cognito).
3.  **Xác định các API endpoints** cần thiết để hỗ trợ tất cả các yêu cầu chức năng được mô tả trong các User Story.
4.  **Thiết kế mô hình dữ liệu chi tiết** cho DynamoDB dựa trên các yêu cầu về sản phẩm, biến thể, đơn hàng và người dùng.
5.  **Chuẩn bị một kế hoạch thực thi kỹ thuật** cho Epic 1, xác định các tác vụ (tasks) cần thiết để hoàn thành từng User Story.

Hãy đảm bảo kiến trúc bạn thiết kế có hiệu suất cao, an toàn, và có khả năng mở rộng.