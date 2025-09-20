# Security and Performance

## Security Requirements

**Frontend Security:**
- **CSP Headers:** Cấu hình Content Security Policy nghiêm ngặt trong `next.config.js` để chỉ cho phép tải tài nguyên từ các nguồn tin cậy, giảm thiểu nguy cơ tấn công XSS.
- **XSS Prevention:** Tận dụng khả năng tự động thoát (escaping) của React. Đối với nội dung do người dùng tạo, sử dụng các thư viện như `dompurify` trước khi hiển thị.
- **Secure Storage:** Lưu trữ JWT (JSON Web Tokens) trong `HttpOnly` cookies để ngăn chặn việc truy cập trái phép thông qua JavaScript phía client.

**Backend Security:**
- **Input Validation:** Sử dụng thư viện `zod` để xác thực và định kiểu cho tất cả dữ liệu đầu vào (payloads, query parameters) tại mỗi Lambda handler.
- **Rate Limiting:** Cấu hình Usage Plans và API Keys trên API Gateway để giới hạn số lượng yêu cầu từ mỗi client, chống lại các cuộc tấn công DoS.
- **CORS Policy:** Định nghĩa chính sách CORS chặt chẽ trong `serverless.yml`, chỉ cho phép các domain frontend đã được phê duyệt truy cập vào API.

**Authentication Security:**
- **Token Storage:** Sử dụng `HttpOnly` cookies để lưu trữ refresh token và access token.
- **Session Management:** Access token có thời gian sống ngắn (ví dụ: 15 phút). Refresh token có thời gian sống dài hơn (ví dụ: 7 ngày) và được sử dụng để lấy access token mới.
- **Password Policy:** Áp dụng chính sách mật khẩu mạnh trong AWS Cognito, yêu cầu độ dài tối thiểu, ký tự đặc biệt, chữ hoa, chữ thường.

## Performance Optimization

**Frontend Performance:**
- **Bundle Size Target:** Giữ kích thước bundle ban đầu dưới `150KB` (sau khi nén) để đảm bảo thời gian tải trang nhanh.
- **Loading Strategy:** Tận dụng tính năng code-splitting tự động của Next.js cho mỗi trang. Sử dụng `next/dynamic` để lazy-load các component không quan trọng.
- **Caching Strategy:** CloudFront sẽ cache các tài sản tĩnh (JS, CSS, hình ảnh). Sử dụng chiến lược `stale-while-revalidate` (SWR) cho việc lấy dữ liệu API để cân bằng giữa tính mới mẻ và hiệu suất.

**Backend Performance:**
- **Response Time Target:** Thời gian phản hồi trung bình (p95) cho các API đọc dưới `200ms`.
- **Database Optimization:** Thiết kế Single-Table của DynamoDB được tối ưu hóa cho các mẫu truy cập chính. Sử dụng Global Secondary Indexes (GSIs) cho các truy vấn phụ.
- **Caching Strategy:** Triển khai Amazon ElastiCache for Redis để cache các truy vấn cơ sở dữ liệu thường xuyên hoặc các dữ liệu có thể tính toán trước.
