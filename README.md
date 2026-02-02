# Cursor Rules Collection

A comprehensive collection of reusable Cursor AI rules for Vue 3 + TypeScript frontend projects.

## What's Inside

This repository contains two types of rules:

- **Project Rules**: Topic-specific rules to copy into your project's `.cursor/rules/` folder
- **User Rules**: Global preferences to add to your Cursor user settings or `.cursorrules` file

## Project Rules

Project rules are organized by topic and designed to be copied into your project's `.cursor/rules/` directory.

### Available Rules

| Topic | Description | Path |
|-------|-------------|------|
| **Localization** | i18n setup, translation keys, language switching | `project-rules/localization/` |
| **Folder Structure** | Directory organization, file naming conventions | `project-rules/folder-structure/` |
| **Types** | TypeScript interfaces, type safety, API response types | `project-rules/types/` |
| **HTTP Requests** | API calls, axios/fetch patterns, error handling | `project-rules/http-requests/` |
| **UI Components** | Component structure, props, composition patterns | `project-rules/ui-components/` |
| **State Management** | Pinia/stores, reactive state patterns | `project-rules/state-management/` |
| **Routing** | Vue Router setup, navigation guards, route patterns | `project-rules/routing/` |
| **Forms & Validation** | Form handling, validation rules, error display | `project-rules/forms-validation/` |
| **Testing** | Unit/e2e testing patterns, test file structure | `project-rules/testing/` |
| **Performance** | Optimization techniques, lazy loading, bundle size | `project-rules/performance/` |
| **GitHub** | Commit messages, PR templates, branch workflow | `project-rules/github/` |

### How to Use Project Rules

1. **Copy the entire folder** to your project:
   ```bash
   cp -r project-rules/localization your-project/.cursor/rules/
   ```

2. **Or copy individual RULE.md files**:
   ```bash
   mkdir -p your-project/.cursor/rules/localization
   cp project-rules/localization/RULE.md your-project/.cursor/rules/localization/
   ```

3. **Customize the rules** to match your project's specific needs

4. **Commit the rules** to your project repository so your team shares the same conventions

### Rule Structure

Each `RULE.md` file includes:

- **Frontmatter**: Description and glob patterns for when the rule applies
- **Sections**: Organized topics with placeholder comments
- **Guidance**: What to add in each section

Example:

```markdown
---
description: Rules for internationalization (i18n) and localization
globs: ["**/*.vue", "**/i18n/**/*"]
---

# Localization & i18n Rules

## Translation Key Management
<!-- Add your rules here -->
```

## User Rules

User rules define your personal coding style and preferences that apply across all projects.

### Available User Rules

- **vue3-typescript.md**: Comprehensive Vue 3 + TypeScript development rules

### How to Use User Rules

**Option 1: Cursor User Settings (Recommended)**

1. Open Cursor Settings (`Cmd/Ctrl + ,`)
2. Search for "Rules for AI"
3. Paste the content from `user-rules/vue3-typescript.md`

**Option 2: Global .cursorrules File**

```bash
cp user-rules/vue3-typescript.md ~/.cursorrules
```

See [`user-rules/README.md`](user-rules/README.md) for more details.

## Getting Started

### Quick Start

1. **Clone this repository**:
   ```bash
   git clone <your-repo-url> cursor-rules
   cd cursor-rules
   ```

2. **Set up user rules** (one time):
   ```bash
   # Copy to Cursor user settings or
   cp user-rules/vue3-typescript.md ~/.cursorrules
   ```

3. **Copy project rules** to your project:
   ```bash
   # Copy all rules
   cp -r project-rules your-project/.cursor/rules/
   
   # Or copy specific rules
   cp -r project-rules/localization your-project/.cursor/rules/
   cp -r project-rules/types your-project/.cursor/rules/
   ```

4. **Customize** the rules to match your project's needs

### Customization

These rules are templates. You should:

1. **Fill in the placeholder sections** with your specific conventions
2. **Remove sections** that don't apply to your project
3. **Add new sections** for project-specific patterns
4. **Update glob patterns** to match your file structure

## Rule Categories Explained

### When to Use Each Rule

- **Localization**: Multi-language apps with i18n
- **Folder Structure**: Any project (define your conventions)
- **Types**: All TypeScript projects
- **HTTP Requests**: Apps with API calls
- **UI Components**: All Vue projects
- **State Management**: Apps with Pinia or complex state
- **Routing**: Multi-page Vue apps with Vue Router
- **Forms & Validation**: Apps with user input
- **Testing**: Projects with test suites
- **Performance**: Production apps needing optimization
- **GitHub**: Teams using Git workflows

## Best Practices

### Project Rules

- Keep rules **specific and actionable**
- Include **code examples** when helpful
- Update rules as your project evolves
- Make rules **enforceable** (not just suggestions)
- Use **glob patterns** to target specific files

### User Rules

- Focus on **personal preferences** that apply everywhere
- Keep them **framework/stack agnostic** when possible
- Update them as you learn new patterns
- Don't duplicate what's in project rules

## Contributing

This is a personal collection, but feel free to:

1. Fork this repository
2. Customize for your needs
3. Share your own rule templates
4. Submit improvements via PR

## Project Structure

```
cursor-rules/
├── README.md                          # This file
├── project-rules/                     # Rules for .cursor/rules/
│   ├── localization/
│   │   └── RULE.md
│   ├── folder-structure/
│   │   └── RULE.md
│   ├── types/
│   │   └── RULE.md
│   ├── http-requests/
│   │   └── RULE.md
│   ├── ui-components/
│   │   └── RULE.md
│   ├── state-management/
│   │   └── RULE.md
│   ├── routing/
│   │   └── RULE.md
│   ├── forms-validation/
│   │   └── RULE.md
│   ├── testing/
│   │   └── RULE.md
│   ├── performance/
│   │   └── RULE.md
│   └── github/
│       └── RULE.md
└── user-rules/                        # Global user preferences
    ├── README.md
    └── vue3-typescript.md
```

## Resources

- [Cursor Documentation](https://cursor.sh/docs)
- [Vue 3 Documentation](https://vuejs.org/)
- [TypeScript Documentation](https://www.typescriptlang.org/)
- [Cursor Rules Guide](https://cursor.sh/docs/rules)

## License

MIT - Feel free to use and modify for your projects.
