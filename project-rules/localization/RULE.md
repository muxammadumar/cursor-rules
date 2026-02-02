---
description: Internationalization setup (if needed for admin panel)
globs: ["**/*.vue", "**/i18n/**/*", "**/locales/**/*"]
---

# Localization & i18n Rules

> **Note**: This section is added as a template. Remove if your admin panel doesn't require multi-language support.

## Setup  

If i18n is needed:

```typescript
// i18n/index.ts
import { createI18n } from 'vue-i18n'
import en from './locales/en.json'
import ar from './locales/ar.json'

export const i18n = createI18n({
  legacy: false,
  locale: 'en',
  fallbackLocale: 'en',
  messages: { en, ar }
})
```

## Usage in Components  

```vue
<script setup lang="ts">
const { t } = useI18n()
</script>

<template>
  <h1>{{ t('orders.title') }}</h1>
  <p>{{ t('orders.count', { count: orders.length }) }}</p>
</template>
```

## Translation Keys  

**Structure**:

```json
{
  "orders": {
    "title": "Orders",
    "create": "Create Order",
    "status": {
      "pending": "Pending",
      "completed": "Completed"
    }
  }
}
```

**Naming**: Use dot notation, organize by domain

## Best Practices  

- Avoid hardcoded strings in templates
- Use translation keys for all user-facing text
- Store locale preference in localStorage
- Provide language switcher in UI if multi-language is needed

**If your admin panel is English-only, remove this entire folder.**
