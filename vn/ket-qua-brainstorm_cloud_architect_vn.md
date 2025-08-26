# Kết quả Buổi Brainstorm

**Ngày họp:** 25/08/2025
**Người điều phối:** Chuyên viên Phân tích Kinh doanh Mary
**Người tham gia:** User

---

## Tóm tắt

**Chủ đề:** Xây dựng một trang web thương mại điện tử bán nước hoa có hiệu năng cao, khả năng mở rộng, với kho sản phẩm ban đầu là 350 sản phẩm.

**Mục tiêu buổi họp:** Mục tiêu chính là tập trung vào các giải pháp kỹ thuật để đảm bảo tốc độ tải trang nhanh và quy trình thanh toán được tối ưu hóa, không có rào cản, đặt nền móng cho việc phát triển Giai đoạn 1.

**Kỹ thuật đã sử dụng:**
1.  **Brainstorming Ngược (Reverse Brainstorming):** Để chủ động xác định các vấn đề tiềm ẩn có thể làm suy giảm hiệu năng và trải nghiệm người dùng.
2.  **Phân tích Lợi ích - Chi phí - Giảm thiểu:** Để đánh giá các giải pháp được đề xuất và chọn ra kiến trúc kỹ thuật tối ưu nhất.

**Chủ đề & Quyết định chính:**
*   **Hiệu năng là tối quan trọng:** Xác định hình ảnh không được tối ưu và việc tải dữ liệu không hiệu quả là những mối đe dọa lớn nhất đối với tốc độ trang web.
*   **Quy trình thanh toán không rào cản là cốt yếu:** Xác định việc bắt buộc đăng nhập, các biểu mẫu phức tạp và chi phí ẩn là những yếu tố chính ngăn cản khách hàng.
*   **Kiến trúc ưu tiên Serverless (Serverless-First) trên AWS là con đường tối ưu:** Cách tiếp cận này tối đa hóa hiệu quả chi phí (tận dụng các gói Miễn phí rộng rãi), hiệu năng và khả năng mở rộng đồng thời giảm thiểu chi phí vận hành.

---

## Rủi ro & Vấn đề đã xác định (Brainstorming Ngược)

### 1. Suy giảm Hiệu năng Website
*   **Vấn đề:** Sử dụng các tệp ảnh gốc, dung lượng lớn, chưa được tối ưu trực tiếp trên trang web.
*   **Vấn đề:** Tải tất cả 350 ảnh sản phẩm ngay khi tải trang lần đầu, bất kể tương tác của người dùng (tức là không có "tải lười" - lazy loading).
*   **Vấn đề:** Lưu trữ các tài sản tĩnh (ảnh, CSS, JS) trên một máy chủ gốc duy nhất đặt ở xa cơ sở người dùng mục tiêu tại Việt Nam.

### 2. Từ bỏ Quy trình Thanh toán
*   **Vấn đề:** Bắt buộc người dùng tạo tài khoản hoặc đăng nhập trước khi họ có thể mua hàng.
*   **Vấn đề:** Yêu cầu người dùng điền vào các biểu mẫu dài, phức tạp với những thông tin không cần thiết.
*   **Vấn đề:** Gây bất ngờ cho người dùng bằng các khoản phí vận chuyển hoặc thuế không mong muốn chỉ ở bước cuối cùng của quy trình thanh toán.

---

## Kiến trúc Kỹ thuật & Giải pháp đề xuất

### Kiến trúc đề xuất: **Ưu tiên Serverless trên AWS**

Kiến trúc này được chọn vì phù hợp với các yêu cầu chính của dự án: hiệu năng cao, khả năng mở rộng và hiệu quả chi phí tối đa cho giai đoạn đầu.

**Sơ đồ:**
```
Người dùng (Trình duyệt)
      │
      ▼
┌──────────────────┐
│   AWS CloudFront   │ (CDN cho Nội dung tĩnh & API)
└─────────┬────────┘
          │
    ┌─────┴──────┐
    │            │
    ▼ (Tĩnh)     ▼ (Yêu cầu API động)
┌───────────┐   ┌────────────────┐
│ S3 Bucket │   │  API Gateway   │
└───────────┘   └────────┬───────┘
                         │
                         ▼
                  ┌────────────────┐
                  │  AWS Lambda    │ (Logic nghiệp vụ)
                  └───────┬────────┘
            ┌─────────────┴──────────────┐
            │                            │
            ▼                            ▼
      ┌──────────┐                 ┌───────────┐
      │ DynamoDB │                 │  Cognito  │ (Quản lý người dùng)
      └──────────┘                 └───────────┘
```

### Phân tích và Lý giải các thành phần

*   **Lưu trữ Frontend (S3 + CloudFront):**
    *   **Lợi ích:** Cung cấp tốc độ hàng đầu bằng cách phục vụ các tệp tĩnh (HTML, CSS, JS, ảnh) từ mạng lưới toàn cầu của CloudFront, với một Điểm hiện diện (Point of Presence) tại Việt Nam. Chi phí cực thấp và khả năng mở rộng vô hạn.
    *   **Chi phí:** Tối thiểu. Được bao gồm trong Gói miễn phí của AWS (1TB truyền dữ liệu/tháng).
    *   **Giảm thiểu:** Kiến trúc này giải quyết trực tiếp các vấn đề đã xác định về tốc độ tải tài sản và vị trí máy chủ.

*   **Logic Backend (API Gateway + AWS Lambda):**
    *   **Lợi ích:** Mô hình "trả tiền theo lần sử dụng". Code chỉ chạy khi có yêu cầu API, nghĩa là không tốn chi phí cho thời gian chờ. Tự động mở rộng để xử lý các đợt tăng đột biến lưu lượng truy cập mà không cần can thiệp thủ công. Loại bỏ gánh nặng quản lý máy chủ.
    *   **Chi phí:** Tối thiểu. Được bao gồm trong Gói miễn phí (1 triệu yêu cầu/tháng cho cả hai dịch vụ). Điều này hiệu quả hơn nhiều về chi phí so với một máy chủ EC2 chạy liên tục cho một trang web mới.
    *   **Giảm thiểu:** Cung cấp một bộ máy có khả năng mở rộng, hiệu quả về chi phí cho tất cả các chức năng thương mại điện tử cốt lõi (tìm kiếm, quản lý giỏ hàng, thanh toán).

*   **Cơ sở dữ liệu (Amazon DynamoDB):**
    *   **Lợi ích:** Một cơ sở dữ liệu NoSQL được quản lý hoàn toàn, không máy chủ, cung cấp độ trễ chỉ vài mili giây. Kết hợp hoàn hảo với Lambda cho các ứng dụng hiệu năng cao.
    *   **Chi phí:** Tối thiểu. Được bao gồm trong Gói miễn phí (25GB dung lượng lưu trữ, ~200 triệu yêu cầu/tháng).
    *   **Giảm thiểu:** Cung cấp một cơ sở dữ liệu nhanh và có khả năng mở rộng cho sản phẩm, đơn hàng và dữ liệu người dùng.

*   **Quản lý người dùng (Amazon Cognito):**
    *   **Lợi ích:** Giảm tải công việc phức tạp và quan trọng của việc xây dựng và duy trì xác thực người dùng (đăng ký, đăng nhập, đặt lại mật khẩu). An toàn và được quản lý hoàn toàn.
    *   **Chi phí:** Tối thiểu. Miễn phí cho 50,000 người dùng hoạt động hàng tháng đầu tiên.
    *   **Giảm thiểu:** Cho phép trực tiếp một luồng "thanh toán với tư cách khách" mượt mà trong khi vẫn cung cấp một cách an toàn, dễ dàng cho người dùng tạo tài khoản nếu họ muốn.

---

## Kế hoạch hành động & Các bước tiếp theo

1.  **Hoàn thiện Danh sách Tính năng Giai đoạn 1:** Tinh chỉnh các tính năng cốt lõi cần thiết để ra mắt dựa trên kiến trúc này.
2.  **Thiết lập Môi trường AWS:** Tạo các S3 bucket cần thiết, cấu hình CloudFront, thiết lập bảng DynamoDB và khởi tạo một Cognito User Pool.
3.  **Phát triển API Backend:** Bắt đầu viết các hàm Lambda cho các chức năng cốt lõi (ví dụ: `getProduct`, `createOrder`).
4.  **Phát triển Ứng dụng Frontend:** Xây dựng giao diện người dùng sẽ sử dụng API backend.
5.  **Triển khai Quy trình Tối ưu hóa Hình ảnh:** Tạo hàm Lambda được kích hoạt bởi việc tải lên S3 để tự động hóa việc xử lý hình ảnh.
