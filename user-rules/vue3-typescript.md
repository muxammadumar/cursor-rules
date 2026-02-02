# Vue 3 + TypeScript User Rules

This file contains global user rules that apply across all Vue 3 + TypeScript projects.

## General Behavior

- Always plan first before writing code
- Explain the plan briefly and ask for confirmation before coding
- If you are not at least 90% sure, ask a clarifying question
- Do not make assumptions about requirements
- Prefer correctness and clarity over speed

## Framework & Stack

- Vue 3 only
- Always use Composition API
- Always use `<script setup lang="ts">`
- Never use Options API
- TypeScript is mandatory in all frontend code

## TypeScript Rules

- Avoid `any` completely
- Use explicit interfaces and types
- Type all props, emits, and composables
- Do not assume API response shapes
- Prefer readable types over overly clever generics

## Code Style

- Prefer arrow functions
- Use early returns
- Avoid deep nesting
- Keep functions small and single-purpose
- Strongly follow DRY principles
- Extract reusable logic instead of duplicating code

## State & Logic

- Prefer composables for shared logic
- Avoid logic inside templates
- Prefer computed properties over watchers
- Avoid unnecessary reactivity

## Styling

- Use Tailwind CSS by default
- Use global CSS only when Element Plus is present in the project
- Avoid inline styles unless absolutely necessary
- Keep styling concerns separate from logic

## Naming Conventions

- Components and pages: PascalCase
  - Example: `AuthHeader.vue`, `LoginPage.vue`
- Composables: camelCase starting with `use`
  - Example: `useAuth.ts`
- Assets: lowercase with dashes only
  - Example: `arrow-down.svg`, `logo-dark.png`
- Variables and functions: clear, descriptive names
- Avoid abbreviations unless widely understood

## Error Handling

- Handle errors explicitly
- Never silently ignore errors
- Prefer predictable error states over defensive hacks
- Surface errors clearly for UI handling

## Refactoring

- Improve structure without changing behavior unless instructed
- Preserve public APIs
- Do not refactor aggressively without confirmation
- Ask before making architectural changes

## Performance

- Do not prematurely optimize
- Point out potential performance issues when relevant
- Avoid unnecessary watchers, re-renders, or recomputations

## Communication

- Be concise and technical
- Explain non-obvious decisions briefly
- Clearly state trade-offs when they exist
- Be honest about uncertainty

## Output

- Prefer concise responses and code-only output unless explanation is requested
