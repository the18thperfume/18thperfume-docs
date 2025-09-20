# Frontend Architecture

## Component Architecture

### Component Organization
```
src/
└── components/
    ├── ui/
    │   ├── button.tsx      # Re-exported from Shadcn
    │   └── card.tsx        # Re-exported from Shadcn
    ├── common/
    │   ├── header.tsx
    │   ├── footer.tsx
    │   └── search-bar.tsx
    ├── products/
    │   ├── product-card.tsx
    │   ├── product-list.tsx
    │   └── product-details.tsx
    └── checkout/
        ├── cart-item.tsx
        ├── cart-summary.tsx
        └── shipping-form.tsx
```

## State Management Architecture

### State Structure (Zustand)
```typescript
// src/stores/cart-store.ts
import { create } from 'zustand';

interface CartItem {
  variantId: string;
  quantity: number;
}

interface CartState {
  items: CartItem[];
  addItem: (item: CartItem) => void;
  removeItem: (variantId: string) => void;
  clearCart: () => void;
}

export const useCartStore = create<CartState>((set) => ({
  items: [],
  addItem: (newItem) => set((state) => {
    // logic to add or update item quantity
    return { items: [...state.items, newItem] };
  }),
  removeItem: (variantId) => set((state) => ({
    items: state.items.filter(item => item.variantId !== variantId)
  })),
  clearCart: () => set({ items: [] }),
}));
```

## Frontend Services Layer

### API Client Setup
```typescript
// src/lib/api-client.ts
import axios from 'axios';

const apiClient = axios.create({
  baseURL: process.env.NEXT_PUBLIC_API_URL || '/api/v1',
  headers: {
    'Content-Type': 'application/json',
  },
});

// Interceptor to add auth token
apiClient.interceptors.request.use(config => {
  // Logic to get token from storage
  const token = localStorage.getItem('token');
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});

export default apiClient;
```

### Service Example
```typescript
// src/services/product-service.ts
import apiClient from '@/lib/api-client';
import { Product } from '@/types'; // Assuming types are defined

export const productService = {
  async getProducts(category?: string): Promise<Product[]> {
    const response = await apiClient.get('/products', { params: { category } });
    return response.data;
  },

  async getProductById(id: string): Promise<Product> {
    const response = await apiClient.get(`/products/${id}`);
    return response.data;
  },
};
```
