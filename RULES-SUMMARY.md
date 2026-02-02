# Rules Summary

This document shows how your original rules were distributed and what was added.

## ✅ From Your Original Rules

### folder-structure/RULE.md
- Layer-based architecture (not feature-based)
- All folder responsibilities (components, views, composables, services, stores, types, assets, styles)
- File naming conventions
- Module boundaries

### types/RULE.md
- TypeScript everywhere
- Avoid `any` completely
- All API responses must be typed
- Type safety rules

### http-requests/RULE.md
- All API calls through service layer
- Don't call fetch/axios directly in components
- API responses must be typed
- Handle and propagate errors consistently
- Components handle UI errors only

### ui-components/RULE.md
- Use `<script setup lang="ts">` only
- One component per file
- Keep components focused and small
- No business logic in templates
- Tailwind CSS as default
- Element Plus overrides in global styles
- Component structure guidelines

### state-management/RULE.md
- Use Pinia for global state
- One store per domain
- No direct state mutation outside actions
- Async logic lives in actions only

### performance/RULE.md
- Avoid unnecessary watchers
- Avoid heavy logic in computed properties
- Use lazy loading where appropriate

### github/RULE.md
- Do not change folder structure without confirmation
- Do not rename public APIs without confirmation
- Ask before large refactors

## 📝 Added by Me (Acceptable Matching Rules)

### routing/RULE.md
**Added complete routing guidelines:**
- Lazy loading for all route components
- Navigation guards for auth
- Route naming conventions (kebab-case paths, camelCase names)
- Meta fields for auth/titles
- Path params vs query params usage
- View component patterns

**Reason**: Your rules mentioned "views" as route-level components but didn't specify Vue Router patterns. Added standard Vue 3 routing practices.

---

### forms-validation/RULE.md
**Added form handling patterns:**
- Element Plus form components usage
- Form validation with FormRules
- Submit handler with duplicate prevention
- Form reset patterns
- Custom input v-model implementation

**Reason**: Not in your original rules. Added since admin panels typically have forms, and you use Element Plus.

---

### testing/RULE.md
**Added testing guidelines:**
- Test organization and naming
- Unit testing for composables/components
- Service mocking patterns
- What to test vs skip
- E2E testing basics

**Reason**: Not in your original rules. Added as templates since testing is critical for production apps.

---

### localization/RULE.md
**Added i18n template (optional):**
- Vue i18n setup
- Translation key structure
- Usage in components
- Note: Can be removed if English-only

**Reason**: Not in your original rules. Added as optional template since some admin panels need multi-language support.

---

## 🎯 All Rules Align With Your Principles

Everything added follows your core principles:
- Layer-based architecture
- TypeScript everywhere
- Service layer for API
- No business logic in components
- Pinia for global state
- Composition API only

## 📂 File Organization

```
project-rules/
├── folder-structure/    ← Your architecture rules
├── types/              ← Your TypeScript rules
├── http-requests/      ← Your API layer rules
├── ui-components/      ← Your component rules
├── state-management/   ← Your Pinia rules
├── performance/        ← Your performance rules
├── routing/            ← Added: Vue Router patterns
├── forms-validation/   ← Added: Form patterns
├── testing/            ← Added: Test patterns
├── github/             ← Your collaboration rules
└── localization/       ← Added: Optional i18n

user-rules/
└── vue3-typescript.md  ← Your global preferences
```

## 🚀 Next Steps

1. **Review added rules** in these files:
   - `routing/RULE.md`
   - `forms-validation/RULE.md`
   - `testing/RULE.md`
   - `localization/RULE.md`

2. **Remove if not needed:**
   - Delete `localization/` folder if admin panel is English-only
   - Simplify `testing/` if you don't have tests yet

3. **Copy to your project:**
   ```bash
   cp -r project-rules /path/to/your-admin-panel/.cursor/rules/
   ```

4. **Customize:**
   - Add specific API endpoints
   - Add project-specific patterns
   - Update examples to match your domain
