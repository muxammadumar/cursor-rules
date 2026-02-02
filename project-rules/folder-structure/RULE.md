---
description: Project folder structure and file organization conventions
globs: ["**/*"]
---

# Folder Structure Rules

## Architecture

Use a **layer-based structure**, not feature-based. Organize code by responsibility, not by domain.

## Directory Organization

```
src/
├── components/     # Reusable UI components only, no business/API logic
├── views/          # Route-level components, minimal logic, mostly composition
├── composables/    # Shared reusable logic, no DOM manipulation
├── services/       # All API communication and business logic
├── stores/         # Global state (Pinia), domain-based stores
├── types/          # Shared TypeScript types and interfaces, no runtime logic
├── assets/         # Static files (images, icons, fonts)
└── styles/         # Global styles and UI library overrides only
```

## File Naming Conventions

- **Components**: PascalCase (`AuthHeader.vue`, `LoginPage.vue`)
- **Views/Pages**: PascalCase (`DashboardView.vue`)
- **Composables**: camelCase with `use` prefix (`useAuth.ts`, `useOrders.ts`)
- **Stores**: camelCase with `use` prefix (`useUserStore.ts`)
- **Services**: camelCase (`orderService.ts`, `authService.ts`)
- **Files & folders**: kebab-case (`order-list/`, `api-client.ts`)
- **Assets**: lowercase with dashes (`arrow-down.svg`, `logo-dark.png`)

## Layer Responsibilities

### components/
- Reusable UI components only
- No business logic
- No API calls
- Props in, events out

### views/
- Route-level components
- Minimal logic, mostly composition
- Orchestrate components and composables

### composables/
- Shared reusable logic
- No direct DOM manipulation
- No API calls (unless explicitly a data composable)
- Return reactive state and methods

### services/
- All API communication
- Business logic related to data fetching
- No UI dependencies
- Export functions, not classes

### stores/
- Global state management (Pinia)
- Domain-based organization (one store per domain)
- Async logic in actions only
- No direct state mutation outside actions

### types/
- Shared TypeScript interfaces and types
- API response types
- No runtime logic

### assets/
- Static files only
- Follow naming conventions strictly

### styles/
- Global styles only
- UI library overrides (e.g., Element Plus)
- No component-specific styles

## Module Boundaries

- Do not import from `views/` anywhere (they are entry points)
- Components should not import from `services/` or `stores/` directly
- Composables can use stores and services
- Services are independent, no circular dependencies
- Types can be imported anywhere


