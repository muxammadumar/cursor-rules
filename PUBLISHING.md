# Publishing to NPM

This guide explains how to publish this package to npm.

## Prerequisites

1. **Create an npm account**: https://www.npmjs.com/signup
2. **Login to npm**:
   ```bash
   npm login
   ```

## Before Publishing

### 1. Update package.json

Replace placeholder values:

```json
{
  "name": "@yourusername/cursor-rules-vue3",  // Change to your npm username
  "author": "Your Name <your.email@example.com>",
  "repository": {
    "url": "https://github.com/yourusername/cursor-rules-vue3.git"
  }
}
```

**Package name options:**

- Scoped (recommended): `@yourusername/cursor-rules-vue3`
- Unscoped: `cursor-rules-vue3` (must be unique on npm)

### 2. Choose a Package Name

Check if name is available:

```bash
npm search cursor-rules-vue3
```

### 3. Update Version

Follow semantic versioning:

- `1.0.0` - Initial release
- `1.0.1` - Bug fixes
- `1.1.0` - New features
- `2.0.0` - Breaking changes

### 4. Create GitHub Repository (Optional but Recommended)

```bash
git init
git add .
git commit -m "Initial commit: Cursor rules collection"
git remote add origin https://github.com/yourusername/cursor-rules-vue3.git
git push -u origin main
```

Update the repository URL in `package.json`.

## Publishing Steps

### First Time Publishing

1. **Verify package contents**:
   ```bash
   npm pack --dry-run
   ```

   This shows what files will be included.

2. **Test locally**:
   ```bash
   npm pack
   ```

   This creates a `.tgz` file you can test by installing in another project:
   ```bash
   npm install /path/to/cursor-rules-vue3-1.0.0.tgz
   ```

3. **Publish to npm**:

   For scoped packages (public):
   ```bash
   npm publish --access public
   ```

   For unscoped packages:
   ```bash
   npm publish
   ```

### Updating the Package

1. **Make your changes**

2. **Update version**:
   ```bash
   # Patch release (1.0.0 -> 1.0.1)
   npm version patch
   
   # Minor release (1.0.0 -> 1.1.0)
   npm version minor
   
   # Major release (1.0.0 -> 2.0.0)
   npm version major
   ```

3. **Publish**:
   ```bash
   npm publish --access public
   ```

4. **Push to GitHub**:
   ```bash
   git push && git push --tags
   ```

## Package Configuration Explained

### files field in package.json

Only these files/folders will be included:

```json
"files": [
  "project-rules",
  "user-rules",
  "README.md",
  "RULES-SUMMARY.md",
  "LICENSE"
]
```

### .npmignore

Excludes files from the package (like `.gitignore` but for npm).

## After Publishing

### 1. Verify on npm

Visit: `https://www.npmjs.com/package/@yourusername/cursor-rules-vue3`

### 2. Test Installation

In a new directory:

```bash
npm install @yourusername/cursor-rules-vue3
ls node_modules/@yourusername/cursor-rules-vue3
```

### 3. Update README Badges

Replace `@yourusername` with your actual npm package name in badges.

## Unpublishing (Use with Caution)

⚠️ **Warning**: Unpublishing is permanent and discouraged.

```bash
# Unpublish a specific version (within 72 hours)
npm unpublish @yourusername/cursor-rules-vue3@1.0.0

# Unpublish entire package (within 72 hours, not recommended)
npm unpublish @yourusername/cursor-rules-vue3 --force
```

## Best Practices

1. **Always test before publishing**: Use `npm pack` and test locally
2. **Use semantic versioning**: Follow semver rules strictly
3. **Keep good documentation**: Update README with each release
4. **Tag releases**: Use git tags to track versions
5. **Write a CHANGELOG**: Document changes between versions
6. **Use scoped packages**: Prevents naming conflicts

## Troubleshooting

### Package name already exists

- Choose a different name
- Use a scoped package: `@yourusername/package-name`

### 403 Forbidden error

- Run `npm login` again
- Check if you have permission to publish to that scope

### Files not included in package

- Check `files` field in `package.json`
- Check `.npmignore`
- Use `npm pack --dry-run` to verify

## Useful Commands

```bash
# Check logged in user
npm whoami

# View package info
npm view @yourusername/cursor-rules-vue3

# View all versions
npm view @yourusername/cursor-rules-vue3 versions

# Check package size
npm pack --dry-run
```

## Next Steps

After successful publishing:

1. Share the package link
2. Add installation instructions to your README
3. Create a GitHub release
4. Announce on social media/dev communities
