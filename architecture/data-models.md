# Data Models

## Product

**Purpose:** Đại diện cho một sản phẩm nước hoa trong cửa hàng.

**Key Attributes:**
- `PK`: `PRODUCT#<product_id>` - Khóa chính
- `SK`: `METADATA#<product_id>` - Khóa sắp xếp
- `productId`: string - ID duy nhất của sản phẩm
- `name`: string - Tên sản phẩm
- `description`: string - Mô tả chi tiết
- `brand`: string - Thương hiệu
- `category`: string - Danh mục (e.g., 'Nam', 'Nữ', 'Unisex')
- `tags`: string[] - Các thẻ để tìm kiếm
- `createdAt`: string (ISO 8601) - Ngày tạo
- `updatedAt`: string (ISO 8601) - Ngày cập nhật cuối

### TypeScript Interface
```typescript
interface Product {
  productId: string;
  name: string;
  description: string;
  brand: string;
  category: string;
  tags: string[];
  variants: ProductVariant[]; // Denormalized for quick access
  createdAt: string;
  updatedAt: string;
}
```

### Relationships
- Một `Product` có nhiều `ProductVariant`.

## ProductVariant

**Purpose:** Đại diện cho một biến thể cụ thể của sản phẩm (ví dụ: dung tích khác nhau).

**Key Attributes:**
- `PK`: `PRODUCT#<product_id>` - Khóa chính (cùng PK với Product)
- `SK`: `VARIANT#<variant_id>` - Khóa sắp xếp
- `variantId`: string - ID duy nhất của biến thể
- `productId`: string - ID của sản phẩm cha
- `size`: string - Dung tích (e.g., '50ml', '100ml')
- `price`: number - Giá bán
- `stock`: number - Số lượng tồn kho
- `imageUrl`: string - URL hình ảnh cho biến thể này

### TypeScript Interface
```typescript
interface ProductVariant {
  variantId: string;
  productId: string;
  size: string;
  price: number;
  stock: number;
  imageUrl: string;
}
```

### Relationships
- Thuộc về một `Product`.

## Order

**Purpose:** Đại diện cho một đơn hàng của khách hàng.

**Key Attributes:**
- `PK`: `USER#<user_id>` - Khóa chính
- `SK`: `ORDER#<order_id>` - Khóa sắp xếp
- `orderId`: string - ID duy nhất của đơn hàng
- `userId`: string - ID của người dùng đặt hàng (hoặc 'GUEST')
- `items`: OrderItem[] - Danh sách các sản phẩm trong đơn hàng
- `totalAmount`: number - Tổng giá trị đơn hàng
- `status`: 'pending' | 'paid' | 'shipped' | 'delivered' | 'cancelled' - Trạng thái đơn hàng
- `shippingAddress`: object - Địa chỉ giao hàng
- `createdAt`: string (ISO 8601) - Ngày tạo

### TypeScript Interface
```typescript
interface OrderItem {
  variantId: string;
  productId: string;
  quantity: number;
  price: number; // Price at time of purchase
}

interface Order {
  orderId: string;
  userId: string;
  items: OrderItem[];
  totalAmount: number;
  status: 'pending' | 'paid' | 'shipped' | 'delivered' | 'cancelled';
  shippingAddress: {
    recipientName: string;
    phone: string;
    address: string;
    city: string;
  };
  createdAt: string;
}
```

### Relationships
- Một `Order` thuộc về một `User` (hoặc là đơn hàng của khách vãng lai).
- Một `Order` chứa nhiều `OrderItem`.

## User

**Purpose:** Đại diện cho một tài khoản người dùng.

**Key Attributes:**
- `PK`: `USER#<user_id>` - Khóa chính
- `SK`: `METADATA#<user_id>` - Khóa sắp xếp
- `userId`: string - ID duy nhất (thường là sub từ Cognito)
- `email`: string - Địa chỉ email
- `name`: string - Tên người dùng
- `authProvider`: 'cognito' | 'google' | 'facebook' - Nhà cung cấp xác thực
- `createdAt`: string (ISO 8601) - Ngày tạo

### TypeScript Interface
```typescript
interface User {
  userId: string;
  email: string;
  name: string;
  authProvider: 'cognito' | 'google' | 'facebook';
  createdAt: string;
}
```

### Relationships
- Một `User` có thể có nhiều `Order`.
