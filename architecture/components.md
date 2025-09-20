# Components

## Component Diagram

```mermaid
graph TD
    subgraph "Frontend (Next.js on CloudFront/S3)"
        WebApp[Web Application]
        State["State Management (Zustand)"]
        ServiceLayer[API Service Layer]
        Components["UI Components (Shadcn/ui)"]
    end

    subgraph "Backend (AWS Lambda/API Gateway)"
        ApiGateway[API Gateway]
        AuthFn[Auth Lambda]
        ProductFn[Products Lambda]
        OrderFn[Orders Lambda]
    end

    subgraph "Data Stores (AWS)"
        UserDB[Cognito User Pool]
        AppDB[DynamoDB Table]
        FileStore[S3 Bucket for Images]
    end

    subgraph "External Services"
        SES[Amazon SES]
        Google[Google Sign-In]
    end

    WebApp --> ServiceLayer
    ServiceLayer --> ApiGateway
    Components --> State
    State --> WebApp

    ApiGateway -- /auth/* --> AuthFn
    ApiGateway -- /products/* --> ProductFn
    ApiGateway -- /orders/* --> OrderFn

    AuthFn --> UserDB
    AuthFn -- Integrates with --> Google
    ProductFn --> AppDB
    OrderFn --> AppDB
    OrderFn --> SES

    ProductFn -- Gets image URLs --> FileStore
```

## Component List

### Frontend: Web Application
- **Responsibility:** Cung cấp giao diện người dùng, xử lý tương tác và hiển thị dữ liệu.
- **Key Interfaces:** Tương tác với `API Service Layer` để lấy và gửi dữ liệu.
- **Dependencies:** `API Service Layer`, `State Management`.
- **Technology Stack:** Next.js, React, TypeScript.

### Backend: Products Lambda
- **Responsibility:** Xử lý tất cả logic nghiệp vụ liên quan đến sản phẩm (lấy danh sách, chi tiết, tìm kiếm).
- **Key Interfaces:** Các endpoint API `/products` và `/products/{id}`.
- **Dependencies:** `DynamoDB`.
- **Technology Stack:** Node.js, TypeScript, Serverless Framework.

### Backend: Orders Lambda
- **Responsibility:** Xử lý logic tạo và quản lý đơn hàng, bao gồm cả quy trình thanh toán (giả định).
- **Key Interfaces:** Endpoint API `/orders`.
- **Dependencies:** `DynamoDB`, `Amazon SES` (để gửi email xác nhận).
- **Technology Stack:** Node.js, TypeScript, Serverless Framework.

### Backend: Auth Lambda
- **Responsibility:** Xử lý đăng ký, đăng nhập và các hoạt động liên quan đến xác thực người dùng.
- **Key Interfaces:** Các endpoint API `/auth/*`.
- **Dependencies:** `AWS Cognito`.
- **Technology Stack:** Node.js, TypeScript, Serverless Framework.
