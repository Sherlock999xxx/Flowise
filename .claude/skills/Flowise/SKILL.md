```markdown
# Flowise Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches the core development patterns and workflows used in the Flowise repository, a TypeScript-based project without a specific framework. You'll learn about the project's coding conventions, dependency management workflows, and testing patterns, enabling you to contribute effectively and maintain consistency across the codebase.

## Coding Conventions

### File Naming
- **Style:** camelCase
- **Example:**  
  ```
  userProfile.ts
  dataFetcher.ts
  ```

### Import Style
- **Style:** Relative imports
- **Example:**
  ```typescript
  import { fetchData } from './dataFetcher';
  ```

### Export Style
- **Style:** Named exports
- **Example:**
  ```typescript
  // In dataFetcher.ts
  export function fetchData() { ... }
  ```

### Commit Messages
- **Style:** Conventional commits
- **Prefix Example:** `chore`
- **Example:**  
  ```
  chore: update dependencies in user management package
  ```

## Workflows

### Multi-Package Dependency Upgrade
**Trigger:** When you need to upgrade npm/yarn dependencies across several packages in the repository (often via Dependabot or similar tools).
**Command:** `/upgrade-dependencies`

1. Identify outdated dependencies in each package under `packages/`.
2. Update the version numbers in each `package.json` file for affected packages.
3. Update the main lockfile(s) (`pnpm-lock.yaml`, `package-lock.json`) to reflect new dependency versions.
4. Commit all changed `package.json` and lockfile(s) together, using a conventional commit message.
5. Push the changes and create a pull request for review.

**Files Involved:**
- `packages/*/package.json`
- `packages/*/package-lock.json`
- `pnpm-lock.yaml`

**Example Commit Message:**
```
chore: upgrade dependencies across all packages
```

## Testing Patterns

- **Test File Pattern:** `*.test.*` (e.g., `userService.test.ts`)
- **Framework:** Not explicitly detected; check the repository for more details.
- **Example Test File:**
  ```typescript
  // userService.test.ts
  import { getUser } from './userService';

  test('should fetch user data', () => {
    expect(getUser(1)).toEqual({ id: 1, name: 'Alice' });
  });
  ```

## Commands

| Command                | Purpose                                                           |
|------------------------|-------------------------------------------------------------------|
| /upgrade-dependencies  | Upgrade dependencies across all packages and update lockfiles      |
```
