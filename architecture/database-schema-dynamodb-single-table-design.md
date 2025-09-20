# Database Schema (DynamoDB Single-Table Design)

Sử dụng một bảng duy nhất với các mẫu truy cập được xác định trước.

**Table Name:** `18thPerfumeTable`

**Key Schema:**
- **Partition Key (PK):** `PK` (string)
- **Sort Key (SK):** `SK` (string)

**Global Secondary Indexes (GSIs):**
- **GSI1:**
    - **GSI1PK:** `GSI1PK` (string)
    - **GSI1SK:** `GSI1SK` (string)
    - **Purpose:** Dùng để truy vấn các mục theo loại (ví dụ: lấy tất cả sản phẩm).

**Data Items Examples:**

| PK | SK | GSI1PK | GSI1SK | Data |
| :--- | :--- | :--- | :--- | :--- |
| `USER#user123` | `METADATA#user123` | | | `{ "email": "...", "name": "..." }` |
| `USER#user123` | `ORDER#order456` | | | `{ "totalAmount": 500, "status": "paid", ... }` |
| `PRODUCT#prod789` | `METADATA#prod789` | `PRODUCT` | `2024-07-27T10:00:00Z#prod789` | `{ "name": "...", "brand": "...", "category": "Unisex" }` |
| `PRODUCT#prod789` | `VARIANT#varABC` | | | `{ "size": "100ml", "price": 500, "stock": 10 }` |
| `PRODUCT#prod789` | `VARIANT#varDEF` | | | `{ "size": "50ml", "price": 300, "stock": 25 }` |

**Access Patterns:**
- **Lấy thông tin người dùng và tất cả đơn hàng của họ:** `Query(PK = "USER#user123")`
- **Lấy chi tiết sản phẩm và tất cả biến thể của nó:** `Query(PK = "PRODUCT#prod789")`
- **Lấy tất cả sản phẩm (có thể phân trang):** `Query(GSI1PK = "PRODUCT")`
