# Pre-Publish Checklist

Complete these steps before publishing to npm.

## ✅ Required Steps

### 1. Update package.json

Open `package.json` and replace these placeholders:

```json
{
  "name": "@yourusername/cursor-rules-vue3",
  // Change to: @your-npm-username/cursor-rules-vue3
  // OR use unscoped: cursor-rules-vue3-your-unique-suffix
  
  "author": "Your Name <your.email@example.com>",
  // Add your real name and email
  
  "repository": {
    "url": "https://github.com/yourusername/cursor-rules-vue3.git"
  },
  // Add your GitHub username
  
  "bugs": {
    "url": "https://github.com/yourusername/cursor-rules-vue3/issues"
  },
  // Add your GitHub username
  
  "homepage": "https://github.com/yourusername/cursor-rules-vue3#readme"
  // Add your GitHub username
}
```

### 2. Update LICENSE

Open `LICENSE` and replace:

```
Copyright (c) 2026 [Your Name]
```

With your actual name.

### 3. Update README.md Badges

Replace all instances of `@yourusername/cursor-rules-vue3` with your actual package name:

- npm badge URL
- Installation commands
- All example paths

### 4. Update CHANGELOG.md

Replace the GitHub URL at the bottom with your actual repository URL.

## 📝 Optional but Recommended

### 5. Create GitHub Repository

```bash
# Initialize git if not already done
git init

# Add all files
git add .

# Initial commit
git commit -m "Initial commit: Cursor rules collection for Vue 3 + TypeScript"

# Create repository on GitHub first, then:
git remote add origin https://github.com/your-username/your-repo-name.git
git branch -M main
git push -u origin main
```

### 6. Check Package Name Availability

```bash
npm search your-package-name
```

If results show up, the name is taken. Choose a different name.

### 7. Decide on Package Scope

**Scoped (Recommended)**:
- Format: `@username/package-name`
- Example: `@umar/cursor-rules-vue3`
- Requires: npm username
- Publishing: `npm publish --access public`

**Unscoped**:
- Format: `package-name`
- Example: `cursor-rules-vue3`
- Must be globally unique
- Publishing: `npm publish`

## 🚀 Publishing Steps

### Step 1: Login to npm

```bash
npm login
```

Enter your npm credentials.

### Step 2: Verify Package Contents

```bash
npm pack --dry-run
```

Check that only necessary files are included.

### Step 3: Test Package Locally (Optional)

```bash
npm pack
```

This creates a `.tgz` file. Test it in another project:

```bash
cd /path/to/test-project
npm install /path/to/cursor-rules-vue3-1.0.0.tgz
```

### Step 4: Publish

For scoped package:
```bash
npm publish --access public
```

For unscoped package:
```bash
npm publish
```

### Step 5: Verify

Visit: `https://www.npmjs.com/package/your-package-name`

## 📋 Files Created for NPM

✅ `package.json` - Package metadata and configuration  
✅ `.npmignore` - Files to exclude from package  
✅ `LICENSE` - MIT license  
✅ `.gitignore` - Files to exclude from git  
✅ `CHANGELOG.md` - Version history  
✅ `PUBLISHING.md` - Detailed publishing guide  
✅ This checklist

## ⚠️ Important Notes

1. **Package Name**: Must be unique on npm (check availability first)
2. **Version**: Start with `1.0.0` for initial release
3. **License**: Update with your name before publishing
4. **Repository**: Optional but recommended to link GitHub repo
5. **Scope**: Using `@username/` requires publishing with `--access public`

## 🎯 After Publishing

1. ✅ Verify package appears on npm
2. ✅ Test installation: `npm install your-package-name`
3. ✅ Share the package link
4. ✅ Create a GitHub release (if using GitHub)
5. ✅ Update documentation if needed

## 🆘 Troubleshooting

**Error: Package name already exists**
- Choose a different name or use scoped package

**Error: 403 Forbidden**
- Run `npm login` again
- Check npm username is correct

**Error: Files missing in package**
- Check `files` array in `package.json`
- Check `.npmignore`

## 📚 Resources

- NPM Documentation: https://docs.npmjs.com/
- Semantic Versioning: https://semver.org/
- Keep a Changelog: https://keepachangelog.com/

---

## Quick Commands

```bash
# Check npm login status
npm whoami

# Check package name availability
npm search package-name

# View what will be published
npm pack --dry-run

# Publish scoped package
npm publish --access public

# Publish unscoped package
npm publish

# View published package
npm view your-package-name
```
