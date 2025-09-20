# Testing Strategy

## Testing Pyramid
```text
      E2E Tests (Cypress)
      /        \
Integration Tests (Jest, Supertest, React Testing Library)
/                     \
Frontend Unit Tests (Jest)   Backend Unit Tests (Jest)
```

## Test Organization

### Frontend Tests (`18thperfume-frontend`)
```
src/
└── components/
    └── products/
        ├── product-card.tsx
        └── __tests__/
            └── product-card.test.tsx # Unit test for ProductCard
cypress/
└── e2e/
    └── auth.cy.ts # E2E test for authentication flow
```

### Backend Tests (`18thperfume-backend`)
```
tests/
├── unit/
│   └── core/
│       └── repository.test.ts # Unit test for the repository
└── integration/
    └── handlers/
        └── get-products.test.ts # Integration test for the API endpoint
```

## Test Examples

### Frontend Component Test
```typescript
// src/components/products/__tests__/product-card.test.tsx
import { render, screen } from '@testing-library/react';
import ProductCard from '../product-card';

it('renders product name and price', () => {
  const mockProduct = { name: 'Test Perfume', price: 100 };
  render(<ProductCard product={mockProduct} />);

  expect(screen.getByText('Test Perfume')).toBeInTheDocument();
  expect(screen.getByText('$100')).toBeInTheDocument();
});
```

### Backend API Test
```typescript
// tests/integration/handlers/get-products.test.ts
import request from 'supertest';
const api = request('http://localhost:3001'); // Assuming serverless-offline port

describe('GET /products', () => {
  it('should return a list of products', async () => {
    const response = await api.get('/products');
    expect(response.status).toBe(200);
    expect(Array.isArray(response.body)).toBe(true);
  });
});
```

### E2E Test
```typescript
// cypress/e2e/auth.cy.ts
describe('Authentication', () => {
  it('allows a user to log in and redirects to dashboard', () => {
    cy.visit('/login');
    cy.get('input[name="email"]').type('test@example.com');
    cy.get('input[name="password"]').type('password123');
    cy.get('button[type="submit"]').click();
    cy.url().should('include', '/dashboard');
  });
});
```
