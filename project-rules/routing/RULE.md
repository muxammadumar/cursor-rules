---
description: Vue Router configuration for admin panel
globs: ["**/router/**/*", "**/views/**/*.vue"]
---

# Routing Rules

## Route Configuration

**Structure**

```typescript
const routes: RouteRecordRaw[] = [
  {
    path: '/',
    component: () => import('@/views/DashboardView.vue'),
    meta: { requiresAuth: true }
  },
  {
    path: '/orders',
    component: () => import('@/views/OrdersView.vue'),
    meta: { requiresAuth: true, title: 'Orders' }
  }
]
```

## Naming Conventions

- **Paths**: kebab-case (`/order-details/:id`)
- **Route names**: camelCase (`orderDetails`)
- **View components**: PascalCase with View suffix (`OrderDetailsView.vue`)

## Lazy Loading

**Always lazy load route components**

```typescript
// Good: Lazy loaded
component: () => import('@/views/OrdersView.vue')

// Bad: Eager loaded
import OrdersView from '@/views/OrdersView.vue'
component: OrdersView
```

## Navigation Guards

**Authentication guard  **

```typescript
router.beforeEach((to, from, next) => {
  const authStore = useAuthStore()
  
  if (to.meta.requiresAuth && !authStore.isAuthenticated) {
    next('/login')
  } else {
    next()
  }
})
```

## Meta Fields

Use route meta for:
- `requiresAuth: boolean` - Auth requirement
- `title: string` - Page title
- `roles: string[]` - Required roles
- `layout: string` - Layout component

## Route Parameters

**Path params for resources**

```typescript
'/orders/:id'  // Resource ID
'/users/:userId/orders'  // Nested resource
```

**Query params for filters**

```typescript
'/orders?status=pending&page=2'  // Filters and pagination
```

## Programmatic Navigation

```typescript
// Navigate to new page
router.push({ name: 'orderDetails', params: { id: '123' } })

// Replace current entry
router.replace('/login')

// Go back
router.back()
```

## View Components

**Views are route-level components**
- Located in `views/` folder
- Minimal logic, mostly composition
- Orchestrate components and composables
- Handle route params

```vue
<script setup lang="ts">
const route = useRoute()
const orderId = computed(() => route.params.id as string)

const { order, loading } = useOrder(orderId)
</script>
```
