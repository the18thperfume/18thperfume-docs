# Backend Architecture

## Service Architecture (Serverless)

### Function Organization
```
18thperfume-backend/
└── src/
    ├── handlers/
    │   ├── get-products.ts
    │   ├── get-product-by-id.ts
    │   ├── create-order.ts
    │   └── auth.ts
    ├── core/
    │   ├── db.ts             # DynamoDB client and helpers
    │   └── repository.ts     # Repository pattern implementation
    ├── types/
    │   └── index.ts
    └── serverless.yml        # Serverless Framework configuration
```

### Function Template (Handler)
```typescript
// src/handlers/get-products.ts
import { APIGatewayProxyHandler } from 'aws-lambda';
import { ProductRepository } from '../core/repository';

const repo = new ProductRepository();

export const handler: APIGatewayProxyHandler = async (event) => {
  try {
    const category = event.queryStringParameters?.category;
    const products = await repo.getProductsByCategory(category);

    return {
      statusCode: 200,
      body: JSON.stringify(products),
    };
  } catch (error) {
    // Proper error handling
    return {
      statusCode: 500,
      body: JSON.stringify({ message: 'Internal Server Error' }),
    };
  }
};
```

## Database Architecture

### Data Access Layer (Repository Pattern)
```typescript
// src/core/repository.ts
import { dbClient } from './db'; // Your DynamoDB DocumentClient
import { Product } from '../types';

export class ProductRepository {
  private readonly tableName = process.env.TABLE_NAME!;

  async getProductsByCategory(category?: string): Promise<Product[]> {
    const params = {
      TableName: this.tableName,
      IndexName: 'GSI1',
      KeyConditionExpression: 'GSI1PK = :pk',
      ExpressionAttributeValues: {
        ':pk': 'PRODUCT',
      },
    };
    // Add filter for category if provided
    const result = await dbClient.query(params).promise();
    return result.Items as Product[];
  }
  // ... other methods like getProductById
}
```
