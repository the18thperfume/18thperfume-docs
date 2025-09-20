# Coding Standards

## Critical Fullstack Rules
- **Type Sharing:** Không có package `shared` trong cấu trúc polyrepo. Các loại dữ liệu (types) API sẽ được định nghĩa trong backend và có thể được sao chép hoặc tạo lại ở frontend để đảm bảo sự tách biệt.
- **API Calls:** Luôn thực hiện các lệnh gọi API thông qua `API Service Layer` đã định nghĩa ở frontend. Không bao giờ gọi `fetch` hoặc `axios` trực tiếp từ các component.
- **Environment Variables:** Truy cập các biến môi trường thông qua một module cấu hình tập trung (ví dụ `src/lib/config.ts`), không bao giờ sử dụng `process.env` trực tiếp trong code ứng dụng.
- **Error Handling:** Tất cả các API handler ở backend phải sử dụng middleware xử lý lỗi chung để đảm bảo định dạng lỗi nhất quán.
- **State Updates:** Không bao giờ thay đổi trạng thái trực tiếp. Luôn sử dụng các hàm cập nhật được cung cấp bởi `Zustand`.

## Naming Conventions

| Element | Frontend | Backend | Example |
| :--- | :--- | :--- | :--- |
| Components | PascalCase | - | `ProductCard.tsx` |
| Hooks | camelCase (với tiền tố `use`) | - | `useAuth.ts` |
| API Routes | - | kebab-case | `GET /user-profile` |
| Database Tables | - | PascalCase | `18thPerfumeTable` |
| Functions (Lambda) | - | camelCase | `getProducts.ts` |
