# API Specification

## REST API Specification (OpenAPI 3.0)

```yaml
openapi: 3.0.0
info:
  title: 18th Perfume API
  version: v1
  description: API for the 18th Perfume e-commerce platform.
servers:
  - url: /api/v1
    description: API Gateway base path
paths:
  /products:
    get:
      summary: Lấy danh sách sản phẩm
      parameters:
        - name: category
          in: query
          schema:
            type: string
        - name: limit
          in: query
          schema:
            type: integer
            default: 20
      responses:
        '200':
          description: Danh sách sản phẩm.
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Product'
  /products/{productId}:
    get:
      summary: Lấy chi tiết sản phẩm
      parameters:
        - name: productId
          in: path
          required: true
          schema:
            type: string
      responses:
        '200':
          description: Chi tiết sản phẩm.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Product'
        '404':
          description: Không tìm thấy sản phẩm.
  /cart:
    post:
      summary: Tạo giỏ hàng hoặc thêm sản phẩm vào giỏ hàng
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                variantId:
                  type: string
                quantity:
                  type: integer
      responses:
        '200':
          description: Cập nhật giỏ hàng thành công.
  /orders:
    post:
      summary: Tạo đơn hàng mới (checkout)
      security:
        - bearerAuth: []
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/OrderInput'
      responses:
        '201':
          description: Tạo đơn hàng thành công.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Order'
  /auth/register:
    post:
      summary: Đăng ký người dùng mới
      requestBody:
        #...
  /auth/login:
    post:
      summary: Đăng nhập
      requestBody:
        #...
components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
  schemas:
    Product:
      #... định nghĩa schema dựa trên interface Product
    Order:
      #... định nghĩa schema dựa trên interface Order
    OrderInput:
      #... định nghĩa schema cho việc tạo đơn hàng
```
