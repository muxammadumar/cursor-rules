---
description: Testing guidelines for admin panel
globs: ["**/*.spec.ts", "**/*.test.ts", "**/tests/**/*"]
---

# Testing Rules

> **Note**: Testing rules added as template. Adjust based on your testing strategy.

## Test Organization  

**File naming**:
- Unit tests: `*.spec.ts` or `*.test.ts`
- E2E tests: `*.e2e.ts` or in `tests/e2e/`

**Location**:
- Co-locate unit tests with source files
- E2E tests in dedicated `tests/` folder

## Unit Testing  

**Test composables**:

```typescript
import { describe, it, expect } from 'vitest'
import { useOrders } from '@/composables/useOrders'

describe('useOrders', () => {
  it('fetches orders on mount', async () => {
    const { orders, loading, fetchOrders } = useOrders()
    
    expect(loading.value).toBe(false)
    await fetchOrders()
    expect(orders.value.length).toBeGreaterThan(0)
  })
})
```

**Test components**:

```typescript
import { mount } from '@vue/test-utils'
import OrderCard from '@/components/OrderCard.vue'

it('displays order info', () => {
  const wrapper = mount(OrderCard, {
    props: { order: mockOrder }
  })
  expect(wrapper.text()).toContain(mockOrder.customerName)
})
```

## Mocking  

**Mock services**:

```typescript
vi.mock('@/services/orderService', () => ({
  orderService: {
    getOrders: vi.fn().mockResolvedValue([mockOrder])
  }
}))
```

## What to Test  

**Priority**:
1. Critical business logic
2. Composables with complex logic
3. Form validation
4. Error handling

**Skip**:
- Trivial getters/setters
- Third-party library internals
- Pure UI components with no logic

## Test Naming  

```typescript
describe('Component/Function name', () => {
  it('does something when condition', () => {
    // Test
  })
})
```

## E2E Testing  

If using Playwright/Cypress:

```typescript
test('user can create order', async ({ page }) => {
  await page.goto('/orders')
  await page.click('[data-testid="create-order"]')
  await page.fill('[name="customerName"]', 'John Doe')
  await page.click('[type="submit"]')
  await expect(page.locator('.success-message')).toBeVisible()
})
```
