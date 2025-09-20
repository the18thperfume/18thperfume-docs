# Tech Stack

| Category | Technology | Version | Purpose | Rationale |
| :--- | :--- | :--- | :--- | :--- |
| Frontend Language | TypeScript | ~5.3.3 | Ngôn ngữ chính cho phát triển frontend | Cung cấp type-safety, cải thiện chất lượng mã nguồn và trải nghiệm lập trình viên. |
| Frontend Framework | Next.js | ~14.1.0 | Framework xây dựng giao diện người dùng | Tối ưu hóa cho hiệu suất (SSR, SSG), SEO-friendly, và hệ sinh thái mạnh mẽ. |
| UI Component Library | Shadcn/ui | ~0.8.0 | Thư viện các thành phần UI có thể tái sử dụng | Cung cấp các khối xây dựng UI đẹp, dễ tùy chỉnh và dễ tiếp cận. |
| State Management | Zustand | ~4.5.2 | Quản lý trạng thái global của ứng dụng | Nhẹ, đơn giản, dễ sử dụng và ít boilerplate hơn so với Redux. |
| Backend Language | TypeScript | ~5.3.3 | Ngôn ngữ chính cho phát triển backend | Nhất quán với frontend, cung cấp type-safety cho các hàm Lambda. |
| Backend Framework | Node.js | 20.x | Môi trường thực thi cho backend | Hiệu suất cao cho các tác vụ I/O, hệ sinh thái npm lớn. |
| API Style | REST | OpenAPI 3.0 | Định dạng giao tiếp giữa frontend và backend | Tiêu chuẩn ngành, được hỗ trợ rộng rãi và dễ hiểu. |
| Database | Amazon DynamoDB | On-demand | Cơ sở dữ liệu NoSQL chính | Khả năng mở rộng vô hạn, hiệu suất cao, phù hợp với mô hình serverless. |
| File Storage | Amazon S3 | Standard | Lưu trữ ảnh sản phẩm và các tệp tĩnh khác | Bền bỉ, chi phí thấp, tích hợp tốt với CloudFront để phân phối nội dung. |
| Authentication | AWS Cognito | Serverless | Quản lý người dùng và xác thực | Dịch vụ được quản lý hoàn toàn, hỗ trợ social login, an toàn và có khả năng mở rộng. |
| Frontend Testing | Jest & React Testing Library | latest | Unit & integration testing cho các component React | Tiêu chuẩn cho việc kiểm thử ứng dụng React, tập trung vào hành vi người dùng. |
| Backend Testing | Jest & Supertest | latest | Unit & integration testing cho các hàm Lambda | Kết hợp Jest cho unit test và Supertest để kiểm thử API endpoints. |
| E2E Testing | Cypress | latest | Kiểm thử đầu cuối toàn bộ ứng dụng | Cung cấp trải nghiệm gỡ lỗi tốt và kiểm thử đáng tin cậy trên trình duyệt. |
| IaC Tool | Serverless Framework | ~3.38.0 | Định nghĩa và triển khai cơ sở hạ tầng backend | Đơn giản hóa việc triển khai ứng dụng serverless trên AWS. |
| CI/CD | GitHub Actions | v4 | Tự động hóa build, test và deploy | Tích hợp sẵn với GitHub, dễ dàng cấu hình các quy trình làm việc. |
| CSS Framework | Tailwind CSS | ~3.4.1 | Framework CSS utility-first | Cho phép tạo kiểu nhanh chóng và nhất quán mà không cần rời khỏi HTML. |
