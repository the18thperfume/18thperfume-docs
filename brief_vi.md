# Project Brief: Trang web E-commerce Nước hoa 18thPerfume

## 1. Tóm tắt Điều hành (Executive Summary)

Dự án này nhằm xây dựng một trang web e-commerce chuyên biệt cho mặt hàng nước hoa, với mục tiêu cốt lõi là mang lại hiệu suất vượt trội, khả năng mở rộng linh hoạt và một quy trình thanh toán liền mạch cho người dùng tại Việt Nam. Nền tảng sẽ giải quyết các vấn đề phổ biến như tốc độ tải trang chậm và các rào cản trong thanh toán (ví dụ: bắt buộc đăng nhập). Bằng cách áp dụng kiến trúc Serverless-First trên AWS, chúng ta sẽ cung cấp một trải nghiệm mua sắm nhanh chóng, đáng tin cậy và tối ưu về chi phí, hướng đến cả những người mới tìm hiểu về nước hoa và những khách hàng sành sỏi.

---

## 2. Tuyên bố Vấn đề (Problem Statement)

Các khách hàng tiềm năng khi mua nước hoa trực tuyến tại Việt Nam thường xuyên phải đối mặt với trải nghiệm người dùng kém chất lượng, dẫn đến tỷ lệ từ bỏ cao. Các vấn đề cốt lõi bao gồm:

1.  **Hiệu suất Website Kém:** Nhiều trang web hiện tại có tốc độ tải trang chậm do hình ảnh không được tối ưu và hạ tầng máy chủ ở xa, gây khó chịu và làm mất khách hàng ngay từ những giây đầu tiên.
2.  **Quy trình Thanh toán Phức tạp:** Khách hàng thường bị buộc phải tạo tài khoản, điền các biểu mẫu dài dòng và đối mặt với các chi phí phát sinh (như phí vận chuyển) chỉ hiển thị ở bước cuối cùng. Những rào cản này là nguyên nhân chính gây ra việc từ bỏ giỏ hàng.
3.  **Thiếu Trải nghiệm Chuyên biệt:** Các sàn thương mại điện tử tổng hợp không cung cấp được trải nghiệm mua sắm chuyên sâu và tư vấn cần thiết cho một sản phẩm đặc thù và mang tính cá nhân cao như nước hoa.

Việc không giải quyết triệt để các vấn đề này sẽ làm giảm đáng kể tỷ lệ chuyển đổi, ảnh hưởng tiêu cực đến doanh thu và làm suy giảm uy tín thương hiệu ngay từ giai đoạn đầu.

---

## 3. Giải pháp Đề xuất (Proposed Solution)

Chúng ta sẽ xây dựng một trang web e-commerce chuyên biệt, hiệu suất cao bằng cách áp dụng triệt để kiến trúc **Serverless-First trên nền tảng AWS**. Giải pháp này được thiết kế để giải quyết trực tiếp các vấn đề đã nêu:

1.  **Tối ưu Tốc độ và Hiệu suất:**
    *   Toàn bộ nội dung tĩnh (hình ảnh, CSS, JS) sẽ được phân phối qua mạng lưới toàn cầu của **AWS CloudFront**, đảm bảo tốc độ tải trang nhanh nhất có thể cho người dùng tại Việt Nam.
    *   Logic nghiệp vụ (quản lý giỏ hàng, tìm kiếm, xử lý đơn hàng) sẽ được thực thi bởi **AWS Lambda**, một dịch vụ chỉ chạy khi có yêu cầu, giúp hệ thống phản hồi tức thì và tự động co giãn theo lưu lượng truy cập.

2.  **Xây dựng Quy trình Thanh toán Liền mạch:**
    *   Triển khai tính năng **"Guest Checkout"** (thanh toán không cần đăng nhập) làm trọng tâm, loại bỏ rào cản lớn nhất cho khách hàng mới.
    *   Sử dụng **Amazon Cognito** để quản lý tài khoản người dùng một cách an toàn và hiệu quả, cho phép đăng nhập tùy chọn qua mạng xã hội mà không làm gián đoạn luồng mua sắm.

3.  **Nền tảng Vững chắc và Tiết kiệm:**
    *   Sử dụng **Amazon S3** để lưu trữ tài sản và **Amazon DynamoDB** làm cơ sở dữ liệu, cung cấp khả năng lưu trữ và truy xuất dữ liệu cực nhanh, đáng tin cậy.
    *   Kiến trúc này tận dụng tối đa các gói miễn phí (Free Tier) của AWS, giúp **giảm thiểu chi phí vận hành xuống gần như bằng không** trong giai đoạn đầu, trong khi vẫn đảm bảo khả năng mở rộng vô hạn khi doanh nghiệp phát triển.

Tầm nhìn của giải pháp là tạo ra một nền tảng không chỉ giải quyết các vấn đề hiện tại mà còn là một tài sản kỹ thuật linh hoạt, cho phép chúng ta dễ dàng phát triển và tích hợp các tính năng mới trong tương lai mà không cần tái cấu trúc hệ thống.

---

## 4. Người dùng Mục tiêu (Target Users)

#### Phân khúc chính: **Người mua sắm trực tuyến thông thường**

*   **Hồ sơ:** Đây là nhóm người dùng đa dạng, quen thuộc với việc mua sắm online. Họ có thể đang tìm mua một chai nước hoa cụ thể, mua quà tặng, hoặc mua lại sản phẩm đã dùng.
*   **Nhu cầu & Điểm đau:** Họ ưu tiên sự **tiện lợi, tốc độ và sự tin cậy**. Các điểm đau của họ là quy trình thanh toán phức tạp, website chậm, và thông tin sản phẩm không rõ ràng. Họ đánh giá cao các tính năng như "Guest Checkout", đăng nhập bằng mạng xã hội và giao diện trực quan.
*   **Mục tiêu:** Hoàn thành việc mua sắm một cách nhanh chóng và không gặp trở ngại.

#### Phân khúc phụ: **Người yêu thích và tìm hiểu nước hoa**

*   **Hồ sơ:** Nhóm người dùng này có kiến thức hoặc đam mê về nước hoa. Họ không chỉ mua hàng mà còn tìm kiếm, khám phá các mùi hương mới, thương hiệu Niche, hoặc tìm hiểu sâu về các tầng hương.
*   **Nhu cầu & Điểm đau:** Họ cần các công cụ **khám phá và so sánh mạnh mẽ**. Điểm đau của họ là các trang web thiếu bộ lọc chi tiết (theo nồng độ, phong cách, nhóm hương) và không có nội dung chuyên sâu. Họ sẽ là người sử dụng chính của các tính năng như bộ lọc nâng cao, so sánh sản phẩm, và trong tương lai là "Scent Finder Quiz".
*   **Mục tiêu:** Tìm kiếm và khám phá được sản phẩm ưng ý nhất dựa trên các tiêu chí phức tạp, đồng thời học hỏi thêm về thế giới nước hoa.

---

## 5. Mục tiêu & Các chỉ số Thành công (Goals & Success Metrics)

#### **Mục tiêu Kinh doanh**

*   **Ra mắt thành công MVP (Sản phẩm Khả thi Tối thiểu)** với các tính năng cốt lõi trong khung thời gian dự kiến để nhanh chóng tiếp cận thị trường.
*   **Tối ưu hóa Tỷ lệ Chuyển đổi** bằng cách loại bỏ các rào cản trong trải nghiệm người dùng, đặc biệt là ở quy trình thanh toán.
*   **Giữ chi phí vận hành ở mức tối thiểu** trong giai đoạn đầu bằng cách tận dụng kiến trúc serverless và các gói miễn phí của AWS.

#### **Chỉ số Thành công của Người dùng**

*   Người dùng có thể **hoàn thành một giao dịch mua hàng (từ lúc vào trang đến lúc thanh toán thành công) trong dưới 2 phút**.
*   Người dùng có thể **dễ dàng tìm thấy sản phẩm họ muốn** thông qua cả thanh điều hướng và chức năng tìm kiếm.
*   Người dùng cảm thấy **tin tưởng và an toàn** khi thực hiện giao dịch trên trang web.

#### **Các chỉ số Hiệu suất chính (KPIs)**

*   **Tỷ lệ chuyển đổi (Conversion Rate):** % người dùng hoàn thành mua hàng. Mục tiêu ban đầu: > 1.5%.
*   **Tỷ lệ từ bỏ giỏ hàng (Cart Abandonment Rate):** % người dùng thêm sản phẩm vào giỏ nhưng không hoàn thành thanh toán. Mục tiêu: < 60%.
*   **Thời gian tải trang trung bình (Average Page Load Time):** Thời gian để các trang chính (trang chủ, trang sản phẩm) hiển thị đầy đủ. Mục tiêu: < 2 giây.
*   **Điểm Google PageSpeed Insights:** Một chỉ số tổng hợp về hiệu suất và trải nghiệm người dùng. Mục tiêu: > 90 điểm trên di động.

---

## 6. Phạm vi MVP (MVP Scope)

#### **Các tính năng Cốt lõi (Must-Have)**

*   **Quản lý & Phân loại Sản phẩm:** Cho phép quản trị viên đăng tải, cập nhật sản phẩm và người dùng có thể duyệt sản phẩm qua các danh mục rõ ràng (giới tính, dòng sản phẩm, thương hiệu).
*   **Tìm kiếm Thông minh & Gợi ý:** Cung cấp một ô tìm kiếm hoạt động hiệu quả, với các gợi ý tức thì để giúp người dùng tìm sản phẩm nhanh hơn.
*   **Giỏ hàng & Thanh toán:** Một quy trình hoàn chỉnh từ việc thêm sản phẩm vào giỏ hàng, điền thông tin, cho đến thanh toán thành công. Hỗ trợ **"Guest Checkout"** và các cổng thanh toán phổ biến (COD, ZaloPay, Momo, VNPAY) là bắt buộc.
*   **Quản lý Tài khoản Thành viên:** Cho phép người dùng tùy chọn đăng ký/đăng nhập (bao gồm cả qua mạng xã hội) để quản lý thông tin và xem lại lịch sử đơn hàng.
*   **Trang Quản trị (Admin Panel):** Giao diện cơ bản cho phép quản trị viên quản lý các khía cạnh cốt lõi: sản phẩm, đơn hàng và thành viên.

#### **Nằm ngoài Phạm vi MVP (Out of Scope for MVP)**

*   **Các tính năng "Nên có" (Should-have):** Chatbot, Hệ thống Coupon/Voucher, Đánh giá sản phẩm, Wishlist, Gợi ý sản phẩm liên quan, Bộ lọc nâng cao, So sánh sản phẩm.
*   **Các tính năng "Có thể có" (Could-have):** Công cụ "Scent Finder Quiz", Chương trình khách hàng thân thiết.
*   **Các tính năng "Sẽ không có" (Won't-have):** Vận chuyển quốc tế, Tích hợp với các sàn TMĐT khác.

#### **Tiêu chí Thành công của MVP**

*   Nền tảng được ra mắt ổn định, không có lỗi nghiêm trọng.
*   Tất cả các tính năng trong danh sách "Must-have" hoạt động đúng như mong đợi.
*   Đạt được các KPI hiệu suất ban đầu đã đề ra (ví dụ: thời gian tải trang < 2 giây, tỷ lệ chuyển đổi > 1.5%).

---

## 7. Tầm nhìn sau MVP (Post-MVP Vision)

#### **Các tính năng Giai đoạn 2**

*   **Tăng cường Tương tác & Tin cậy:** Tích hợp **Chatbot** tư vấn, hệ thống **Đánh giá & Xếp hạng Sản phẩm**, và chức năng **Danh sách Yêu thích (Wishlist)**.
*   **Thúc đẩy Doanh số:** Xây dựng **Hệ thống Coupon/Voucher** và triển khai các module **Gợi ý Sản phẩm Liên quan**.
*   **Nâng cao Trải nghiệm Khám phá:** Phát triển **Bộ lọc & Sắp xếp Nâng cao** và công cụ **So sánh Sản phẩm**.
*   **Cá nhân hóa:** Ra mắt công cụ "Tìm mùi hương cho bạn" (**Scent Finder Quiz**) để dẫn dắt và tư vấn cho người dùng mới.

#### **Tầm nhìn Dài hạn**

Trong 1-2 năm tới, mục tiêu là phát triển 18thPerfume từ một trang web bán hàng hiệu suất cao trở thành **điểm đến hàng đầu và đáng tin cậy nhất cho cộng đồng yêu nước hoa tại Việt Nam**.

#### **Cơ hội Mở rộng**

*   **Phát triển Nội dung:** Xây dựng blog, kênh video review, và các bài viết chuyên sâu về nước hoa.
*   **Chương trình Khách hàng Thân thiết:** Triển khai hệ thống tích điểm, đổi thưởng.
*   **Dịch vụ Trải nghiệm:** Cân nhắc cung cấp các bộ mẫu thử (sample/discovery set).

---

## 8. Các xem xét về Kỹ thuật (Technical Considerations)

#### **Yêu cầu Nền tảng**

*   **Nền tảng mục tiêu:** Web (Tương thích hoàn toàn với cả máy tính để bàn và thiết bị di động).
*   **Hỗ trợ Trình duyệt/HĐH:** Các phiên bản mới nhất của Chrome, Firefox, Safari, và Edge.
*   **Yêu cầu Hiệu suất:** Thời gian tải trang dưới 2 giây.

#### **Ưu tiên Công nghệ**

*   **Frontend:** Một framework JavaScript hiện đại (ví dụ: React, Vue, Svelte).
*   **Backend:** **AWS Lambda** (Node.js hoặc Python) cho logic nghiệp vụ.
*   **Cơ sở dữ liệu:** **Amazon DynamoDB** (NoSQL).
*   **Hosting/Hạ tầng:** **AWS S3** và **AWS CloudFront** (CDN).

#### **Các xem xét về Kiến trúc**

*   **Kiến trúc Dịch vụ:** **Serverless-First, API-driven**.
*   **Yêu cầu Tích hợp:** Tích hợp với các cổng thanh toán phổ biến tại Việt Nam (COD, ZaloPay, Momo, VNPAY).
*   **Bảo mật/Tuân thủ:** **Amazon Cognito** sẽ xử lý toàn bộ việc xác thực và quản lý người dùng.

---

## 9. Các Ràng buộc & Giả định (Constraints & Assumptions)

#### **Các Ràng buộc**

*   **Ngân sách:** Tận dụng tối đa AWS Free Tier để giảm thiểu chi phí.
*   **Thời gian:** Ra mắt MVP nhanh chóng.
*   **Tài nguyên:** Đội ngũ phát triển nhỏ, ưu tiên các dịch vụ được quản lý hoàn toàn.
*   **Kỹ thuật:** Tuân thủ kiến trúc Serverless-First trên AWS.

#### **Các Giả định Chính**

*   Lưu lượng truy cập ban đầu nằm trong giới hạn của AWS Free Tier.
*   Tốc độ và sự tiện lợi là yếu tố quyết định chính của người dùng.
*   Có một thị trường đủ lớn cho một trang web chuyên biệt.
*   Phạm vi tính năng MVP là ổn định.

---

## 10. Rủi ro & Các câu hỏi mở (Risks & Open Questions)

#### **Các Rủi ro Chính**

*   **Rủi ro về Hiệu suất Frontend:** Code frontend không được tối ưu có thể làm chậm trang web.
    *   **Chiến lược Giảm thiểu:**
        1.  **Thiết lập Ngân sách Hiệu suất (Performance Budgeting):** Đặt ra giới hạn cụ thể cho kích thước file, thời gian tải.
        2.  **Tối ưu hóa Tài sản (Asset Optimization):** Áp dụng "code splitting", "lazy loading", và tối ưu hóa hình ảnh.
        3.  **Kiểm tra và Giám sát Thường xuyên:** Tích hợp Google Lighthouse vào quy trình phát triển.
*   **Rủi ro về Phụ thuộc Nhà cung cấp (Vendor Lock-in):** Phụ thuộc sâu vào hệ sinh thái AWS.
*   **Rủi ro về Cạnh tranh:** Khó khăn trong việc thu hút và giữ chân khách hàng.

#### **Các câu hỏi mở**

*   Chiến lược marketing chi tiết để thu hút người dùng đầu tiên là gì?
*   Quy trình sản xuất và quản lý nội dung sẽ được thực hiện như thế nào?
*   Các yêu cầu pháp lý cụ thể tại Việt Nam là gì?

#### **Các lĩnh vực cần nghiên cứu thêm**

*   Phân tích chi tiết các đối thủ cạnh tranh trực tiếp.
*   Nghiên cứu người dùng sâu hơn để xác thực các giả định.
