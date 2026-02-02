# User Rules

User rules are global preferences that apply across all your projects.

## What Are User Rules?

User rules define your personal coding style, preferences, and conventions that should be consistent across all projects you work on. Unlike project rules (which are specific to a single codebase), user rules travel with you.

## How to Use

### Option 1: Cursor User Rules (Recommended)

Add these rules to your Cursor user settings:

1. Open Cursor Settings (Cmd/Ctrl + ,)
2. Search for "Rules for AI"
3. Paste the content from `vue3-typescript.md`

### Option 2: Global .cursorrules File

Create a `.cursorrules` file in your home directory:

```bash
cp vue3-typescript.md ~/.cursorrules
```

## Available User Rules

### vue3-typescript.md

Comprehensive rules for Vue 3 + TypeScript development including:

- Framework preferences (Composition API, script setup)
- TypeScript standards (no any, explicit types)
- Code style (arrow functions, early returns, DRY)
- Naming conventions (PascalCase components, camelCase composables)
- Error handling patterns
- Performance guidelines
- Communication preferences

## Customization

Feel free to modify these rules to match your personal preferences. These are templates to get you started.

## When to Use User Rules vs Project Rules

**User Rules:**
- Personal coding style preferences
- Language/framework choices
- General best practices you always follow
- Communication style with AI

**Project Rules:**
- Project-specific architecture decisions
- Team conventions
- Technology stack for this specific project
- Domain-specific patterns
