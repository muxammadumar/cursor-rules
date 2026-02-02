---
description: Git workflow and collaboration guidelines
globs: ["**/*"]
---

# GitHub Workflow Rules

## Core Principle

**From your rules:**
- Do not change folder structure without confirmation
- Do not rename public APIs without confirmation  
- Ask before large refactors

## Commit Messages  

**Format**: Use conventional commits

```
feat: add order filtering by status
fix: resolve date formatting issue
refactor: extract order logic to composable
docs: update API documentation
chore: update dependencies
```

**Structure**:
- Type: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`
- Scope (optional): `(orders)`, `(auth)`
- Subject: Imperative, present tense

## Branch Management  

**Naming convention**:
```
feature/order-filtering
fix/date-formatting-bug
refactor/extract-order-logic
```

**Workflow**:
- Create branch from `dev`
- Keep branches short-lived
- Delete branch after merge

## Pull Requests  

**Title**: Same format as commits

```
feat: add order filtering by status
```

**Description template**:
```markdown
## What
Brief description of changes

## Why
Reason for changes

## Testing
How to test the changes
```

## Code Review Guidelines  

**What to review**:
- Adherence to folder structure rules
- No business logic in components
- All API calls go through services
- TypeScript types are complete
- No `any` types used

**Give constructive feedback**:
- Explain why something should change
- Suggest alternatives
- Ask questions if unclear

## Merge Strategy  

- **Squash and merge** for feature branches
- Keep commit history clean
- Write clear merge commit message

## Collaboration Rules

**Before making changes**:
- ✅ Confirm folder structure changes
- ✅ Confirm API renames
- ✅ Confirm large refactors

**Safe without confirmation**:
- Bug fixes
- New features following existing patterns
- Documentation updates
- Test additions
