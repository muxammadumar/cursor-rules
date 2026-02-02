---
description: TypeScript everywhere with strict type safety
globs: ["**/*.ts", "**/*.vue", "**/types/**/*"]
---

# TypeScript Types Rules

## Core Principle

**TypeScript is mandatory everywhere**
- No JavaScript files allowed
- Avoid `any` completely
- Use explicit types and interfaces

## Type Location

- **Shared types**: `types/` folder
- **Component-specific**: Co-locate with component if not reused
- **Service-specific**: Define in service file or `types/`
- **Store-specific**: Define in store file or `types/`

## Type Definitions

- Prefer `interface` for object shapes that might be extended
- Use `type` for unions, intersections, and primitives
- Export all shared types from `types/` folder
- No runtime logic in `types/` folder

## Component Types

```typescript
// Type all props explicitly
interface Props {
  userId: string
  isActive?: boolean
}

// Type all emits
interface Emits {
  (e: 'update', value: string): void
  (e: 'close'): void
}
```

## API Response Types

- **All API responses must be typed**
- Define response interfaces in `types/` or service files
- Do not assume API response shapes
- Handle optional/nullable fields explicitly

```typescript
interface OrderResponse {
  id: string
  status: 'pending' | 'completed' | 'cancelled'
  items: OrderItem[]
  createdAt: string
}
```

## Type Safety Rules

- **Never use `any`** - use `unknown` if type is truly unknown
- Type all function parameters and return values
- Use strict null checks
- Prefer type inference for local variables
- Use type guards for runtime validation

## Naming Conventions

- Interfaces: PascalCase (`UserProfile`, `OrderItem`)
- Types: PascalCase (`OrderStatus`, `ApiError`)
- Generic parameters: Single uppercase letter or PascalCase (`T`, `TData`)

## Utility Types

Use built-in TypeScript utilities when appropriate:
- `Partial<T>`, `Required<T>`, `Pick<T>`, `Omit<T>`
- `Record<K, V>` for key-value objects
- Create custom utilities only when necessary
