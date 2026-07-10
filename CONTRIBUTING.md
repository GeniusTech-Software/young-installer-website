# Contributing Guide

## Commit Message Format

This project uses [Conventional Commits](https://www.conventionalcommits.org/) to automatically generate releases and changelogs.

### Commit Message Structure

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

- **feat**: A new feature (triggers a minor version bump)
- **fix**: A bug fix (triggers a patch version bump)
- **docs**: Documentation only changes
- **style**: Changes that don't affect the meaning of the code (white-space, formatting, etc)
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **perf**: A code change that improves performance
- **test**: Adding missing tests or correcting existing tests
- **build**: Changes that affect the build system or external dependencies
- **ci**: Changes to CI configuration files and scripts
- **chore**: Other changes that don't modify src or test files
- **revert**: Reverts a previous commit

### Breaking Changes

To trigger a major version bump, add `BREAKING CHANGE:` in the commit footer or add `!` after the type:

```
feat!: remove support for Node 12

BREAKING CHANGE: Node 12 is no longer supported
```

### Examples

#### Feature (Minor version bump: 1.0.0 → 1.1.0)
```
feat: add Myanmar language support for install steps

Added complete Burmese translations for all installation guide steps
```

#### Bug Fix (Patch version bump: 1.0.0 → 1.0.1)
```
fix: correct QR code generation URL encoding

The QR code now properly encodes special characters in the APK URL
```

#### Documentation (Patch version bump with scope)
```
docs(README): update deployment instructions for Cloudflare Pages
```

#### Breaking Change (Major version bump: 1.0.0 → 2.0.0)
```
feat!: redesign download page layout

BREAKING CHANGE: The page structure has changed significantly.
Custom CSS targeting old classes will break.
```

## Pull Request Process

1. Create a feature branch from `main` or `master`
2. Make your changes with proper commit messages
3. Push your branch and create a Pull Request
4. CI will validate your commits and HTML
5. Once approved and merged, semantic-release will automatically create a new release

## Release Process

Releases are **fully automated** through GitHub Actions:

1. When code is merged to `main` or `master`, the Release workflow runs
2. semantic-release analyzes commit messages since the last release
3. It determines the next version number based on commit types
4. Creates a new Git tag and GitHub Release
5. Updates CHANGELOG.md and package.json
6. Commits these changes back to the repository

### Manual Release (Not Recommended)

If you need to trigger a release manually:

```bash
npm ci
npx semantic-release
```

Make sure you have `GITHUB_TOKEN` environment variable set.

## Development Workflow

### Setup

```bash
# Install dependencies
npm install

# Start local development server
npm run serve
```

### Making Changes

1. Create a feature branch:
   ```bash
   git checkout -b feat/your-feature-name
   ```

2. Make your changes

3. Commit with conventional commit format:
   ```bash
   git commit -m "feat: add new feature"
   ```

4. Push and create a PR:
   ```bash
   git push origin feat/your-feature-name
   ```

## Branch Protection

It's recommended to set up branch protection rules on GitHub:

1. Go to repository Settings → Branches
2. Add a branch protection rule for `main` (or `master`)
3. Enable:
   - ✅ Require a pull request before merging
   - ✅ Require status checks to pass (CI, validate)
   - ✅ Require conversation resolution before merging
   - ✅ Do not allow bypassing the above settings

## Versioning

This project follows [Semantic Versioning](https://semver.org/):

- **MAJOR** (X.0.0): Breaking changes
- **MINOR** (0.X.0): New features (backwards compatible)
- **PATCH** (0.0.X): Bug fixes and documentation updates

## Questions?

If you have questions about the contribution process, please open an issue or contact the maintainers.
