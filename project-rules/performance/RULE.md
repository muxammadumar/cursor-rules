---
description: Performance optimization guidelines
globs: ["**/*.vue", "**/*.ts"]
---

# Performance Rules

## Core Principles

- **Avoid unnecessary watchers**
- **Avoid heavy logic in computed properties**
- **Use lazy loading where appropriate**

## Reactivity Optimization

**Avoid unnecessary watchers**

```typescript
// Good: Use computed
const filteredOrders = computed(() => 
  orders.value.filter(o => o.status === 'active')
)

// Bad: Watcher for simple derivation
watch(orders, () => {
  filteredOrders.value = orders.value.filter(o => o.status === 'active')
})
```

**Avoid heavy logic in computed**

```typescript
// Bad: Expensive operation in computed
const processedData = computed(() => 
  data.value.map(item => expensiveTransform(item))
)

// Good: Process once in action, cache result
async function loadData() {
  const raw = await service.getData()
  processedData.value = raw.map(item => expensiveTransform(item))
}
```

## Component Performance

**Lazy load routes**

```typescript
const routes = [
  {
    path: '/orders',
    component: () => import('@/views/OrdersView.vue')
  }
]
```

**Use v-show vs v-if appropriately**
- `v-if` for conditionals that rarely change
- `v-show` for frequently toggled elements

**Key lists properly**

```vue
<div v-for="order in orders" :key="order.id">
```

## List Rendering

**For large lists (>100 items):**
- Implement pagination
- Use virtual scrolling (vue-virtual-scroller)
- Lazy load images

**Avoid**:
- Rendering thousands of DOM nodes
- Heavy computations per list item

## Debounce User Input

```typescript
import { useDebounceFn } from '@vueuse/core'

const debouncedSearch = useDebounceFn((query: string) => {
  searchOrders(query)
}, 300)
```

## Asset Optimization

- Optimize images before committing
- Use WebP format when possible
- Lazy load images below the fold
- Use SVG for icons

## Bundle Size

- Avoid importing entire libraries
- Use tree-shakeable imports
- Analyze bundle with `vite-bundle-visualizer`
- Remove unused dependencies

```typescript
// Good: Tree-shakeable
import { debounce } from 'lodash-es'

// Bad: Imports everything
import _ from 'lodash'
```

## Avoid Performance Anti-patterns

- Don't watch large objects deeply
- Don't create reactive objects in loops
- Don't use v-for with v-if on same element
- Don't inline large objects in templates
