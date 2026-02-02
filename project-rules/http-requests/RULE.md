---
description: HTTP client configuration and API request patterns
globs: ["**/services/**/*", "**/api/**/*"]
---

# HTTP Requests Rules

## API Layer Architecture

- **All API calls go through the service layer**
- Do not call `fetch`/`axios` directly inside components
- Services live in `services/` folder
- One service per domain (`orderService.ts`, `authService.ts`)

## Service Structure

```typescript
// services/orderService.ts
import { apiClient } from './apiClient'
import type { Order, CreateOrderDto } from '@/types'

export const orderService = {
  async getOrders(): Promise<Order[]> {
    const response = await apiClient.get<Order[]>('/orders')
    return response.data
  },
  
  async createOrder(data: CreateOrderDto): Promise<Order> {
    const response = await apiClient.post<Order>('/orders', data)
    return response.data
  },
  
  async deleteOrder(id: string): Promise<void> {
    await apiClient.delete(`/orders/${id}`)
  }
}
```

## Type Safety

- **All API responses must be typed**
- Define response types in `types/` folder
- Use generics for API client methods
- No `any` types in API layer

```typescript
// types/order.ts
export interface Order {
  id: string
  items: OrderItem[]
  status: 'pending' | 'active' | 'completed'
  createdAt: string
}

export interface CreateOrderDto {
  items: OrderItem[]
}
```

## API Client Configuration

```typescript
// services/apiClient.ts
import axios from 'axios'

export const apiClient = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,
  timeout: 10000,
  headers: {
    'Content-Type': 'application/json'
  }
})

// Request interceptor for auth
apiClient.interceptors.request.use((config) => {
  const token = localStorage.getItem('token')
  if (token) {
    config.headers.Authorization = `Bearer ${token}`
  }
  return config
})

// Response interceptor for errors
apiClient.interceptors.response.use(
  (response) => response,
  (error) => {
    // Handle 401, 403, etc.
    return Promise.reject(error)
  }
)
```

## Error Handling

- **Handle and propagate errors consistently**
- Components handle UI errors only
- Business errors are handled in services or stores
- Always expose error state to the UI

```typescript
// In store action
const error = ref<string | null>(null)
const loading = ref(false)

const fetchOrders = async () => {
  loading.value = true
  error.value = null
  try {
    orders.value = await orderService.getOrders()
  } catch (e) {
    error.value = e instanceof Error ? e.message : 'Unknown error'
    throw e // Propagate if needed
  } finally {
    loading.value = false
  }
}
```

## Request Organization

- Group methods by HTTP verb
- Use async/await, not promises
- Return typed data, not full response objects
- Keep service functions pure (no side effects)

## Authentication

- Token stored in localStorage or secure cookie
- Add auth header via interceptor
- Handle 401 by redirecting to login
- Implement token refresh if needed
