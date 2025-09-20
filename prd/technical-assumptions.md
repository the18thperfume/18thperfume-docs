# Technical Assumptions

## Repository Structure: Polyrepo

*   **Lựa chọn:** Polyrepo (Multi-repo)
*   **Lý do:** Để quản lý và triển khai độc lập giữa hai phần chính của ứng dụng: Frontend (giao diện người dùng, triển khai trên S3/CloudFront) và Backend (logic nghiệp vụ, triển khai trên AWS Lambda). Cách tiếp cận này giúp hai đội (hoặc hai luồng công việc) có thể phát triển song song mà không ảnh hưởng lẫn nhau.

## Service Architecture

*   **Lựa chọn:** Dựa trên kiến trúc Serverless-First của AWS.
*   **Lý do:** Để tận dụng tối đa khả năng mở rộng tự động, tính sẵn sàng cao và chi phí tối ưu của các dịch vụ serverless như AWS Lambda, API Gateway, và DynamoDB.

---
