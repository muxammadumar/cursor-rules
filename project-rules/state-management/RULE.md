---
description: State management patterns using Pinia
globs: ["**/stores/**/*", "**/composables/use*.ts"]
---

# State Management Rules

## Store Organization

- Use **Pinia** for global state only
- One store per domain (`useOrderStore`, `useAuthStore`)
- Name stores with `use` prefix and `Store` suffix
- Domain-based organization, not feature-based

## File Structure

```typescript
// stores/useOrderStore.ts
import { defineStore } from 'pinia'

export const useOrderStore = defineStore('order', () => {
  // State
  const orders = ref<Order[]>([])
  
  // Getters
  const activeOrders = computed(() => 
    orders.value.filter(o => o.status === 'active')
  )
  
  // Actions
  const fetchOrders = async () => {
    // Async logic here
  }
  
  return { orders, activeOrders, fetchOrders }
})
```

## Store Rules

- **No direct state mutation outside store actions**
- All async logic lives in actions only
- Actions can call services for API communication
- Getters for computed/derived state
- Use setup store syntax (not options)

## When to Use Stores

**Use Pinia stores for:**
- Authentication state
- User profile
- Global app settings
- Shared domain data (orders, products)
- Data needed across multiple routes

**Use local state for:**
- Form inputs
- UI toggles
- Component-specific state
- Temporary data

## Composables vs Stores

**Composables:**
- Reusable logic
- Can be stateful but typically instance-based
- No direct global state mutation
- Can use stores internally

**Stores:**
- Global singleton state
- Shared across entire app
- Persistent or cached data
- Domain-based organization

## Accessing Stores

- Call `useXStore()` inside setup or composables
- Never call outside setup (will break SSR/HMR)
- Destructure with `storeToRefs()` to keep reactivity

```typescript
// ❌ Wrong
const { orders } = useOrderStore()

// ✅ Correct
const { orders } = storeToRefs(useOrderStore())
const { fetchOrders } = useOrderStore()
```

## Error Handling

- Handle errors inside store actions
- Expose error state to UI
- Don't silently swallow errors

```typescript
const error = ref<string | null>(null)

const fetchOrders = async () => {
  error.value = null
  try {
    orders.value = await orderService.getOrders()
  } catch (e) {
    error.value = 'Failed to fetch orders'
    throw e
  }
}
```
