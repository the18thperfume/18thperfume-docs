# Monitoring and Observability

## Monitoring Stack
- **Frontend Monitoring:** AWS CloudWatch RUM (Real User Monitoring) để theo dõi hiệu suất thực tế từ người dùng.
- **Backend Monitoring:** AWS CloudWatch Logs, Metrics, và Alarms cho các hàm Lambda và API Gateway.
- **Error Tracking:** Sentry để tổng hợp, theo dõi và cảnh báo lỗi từ cả frontend và backend.
- **Performance Monitoring:** AWS X-Ray để theo dõi và phân tích các yêu cầu từ đầu đến cuối trong hệ thống backend.

## Key Metrics

**Frontend Metrics (CloudWatch RUM & Sentry):**
- Core Web Vitals (LCP, FID, CLS)
- Tỷ lệ lỗi JavaScript
- Thời gian phản hồi API từ phía client
- Các luồng tương tác của người dùng (User flows)

**Backend Metrics (CloudWatch):**
- **API Gateway:** Tỷ lệ yêu cầu (Request rate), Tỷ lệ lỗi (4xx, 5xx), Độ trễ (Latency).
- **Lambda:** Số lần gọi (Invocations), Thời gian thực thi (Duration), Tỷ lệ lỗi, Số lần bị điều tiết (Throttles).
- **DynamoDB:** Read/Write Capacity Units, Throttled Requests.
