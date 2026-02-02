---
description: UI component structure and composition patterns
globs: ["**/components/**/*.vue", "**/views/**/*.vue"]
---

# UI Components Rules

## General Rules

- Always use `<script setup lang="ts">`
- One component per file
- Keep components focused and small
- No business logic inside templates
- No API calls inside components

## Component Structure

```vue
<script setup lang="ts">
// 1. Imports
// 2. Props & Emits
// 3. Composables
// 4. Local state
// 5. Computed
// 6. Methods
// 7. Lifecycle hooks
</script>

<template>
  <!-- Keep logic minimal, use computed/methods -->
</template>

<style scoped>
  /* Prefer Tailwind, use scoped styles sparingly */
</style>
```

## Props & Emits

- Always type props explicitly
- Use TypeScript interfaces for complex props
- Define emits with types
- Provide default values for optional props

```typescript
interface Props {
  orderId: string
  isActive?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  isActive: false
})

const emit = defineEmits<{
  update: [orderId: string]
  delete: []
}>()
```

## Components vs Views

**components/**
- Reusable UI components only
- No business logic
- No API calls
- Props in, events out
- Can be used anywhere

**views/**
- Route-level components only
- Minimal logic, mostly composition
- Orchestrate components and composables
- Never imported by other components

## Styling

- **Tailwind CSS** is the default
- Use scoped styles only when Tailwind is insufficient
- **Element Plus** overrides go in `styles/` folder, not components
- Avoid inline styles unless absolutely necessary
- Keep styling concerns separate from logic

## Composition Patterns

- Extract reusable logic into composables
- Use composables for complex logic
- Keep component code focused on presentation
- Prefer composition over deep component hierarchies

## Accessibility

- Use semantic HTML elements
- Add ARIA labels where needed
- Ensure keyboard navigation works
- Test focus management
