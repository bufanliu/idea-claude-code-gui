---
name: idea-claude-code-gui-conventions
description: Development conventions and patterns for idea-claude-code-gui. Java project with mixed commits.
---

# Idea Claude Code Gui Conventions

> Generated from [bufanliu/idea-claude-code-gui](https://github.com/bufanliu/idea-claude-code-gui) on 2026-03-16

## Overview

This skill teaches Claude the development patterns and conventions used in idea-claude-code-gui.

## Tech Stack

- **Primary Language**: Java
- **Architecture**: type-based module organization
- **Test Location**: mixed
- **Test Framework**: vitest

## When to Use This Skill

Activate this skill when:
- Making changes to this repository
- Adding new features following established patterns
- Writing tests that match project conventions
- Creating commits with proper message format

## Commit Conventions

Follow these commit message conventions based on 8 analyzed commits.

### Commit Style: Mixed Style

### Prefixes Used

- `fix`
- `feat`
- `docs`
- `refactor`

### Message Guidelines

- Average message length: ~60 characters
- Keep first line concise and descriptive
- Use imperative mood ("Add feature" not "Added feature")


*Commit message example*

```text
docs: update installation section position and plugin link in README
```

*Commit message example*

```text
feat: add GitHub repo section to community settings and default autoOpenFile to false
```

*Commit message example*

```text
fix(permission): READ_ONLY tools require confirmation in default mode, auto-approve in acceptEdits mode
```

*Commit message example*

```text
chore: rename project to CC GUI and bump version to 0.2.9
```

*Commit message example*

```text
refactor: split FileHandler, HistoryHandler, ClaudeHistoryReader and App.tsx into focused modules
```

*Commit message example*

```text
Merge pull request #676 from zhukunpenglinyutong/feature/v0.2.9
```

*Commit message example*

```text
Merge pull request #674 from zhukunpenglinyutong/feature/v0.2.9
```

*Commit message example*

```text
docs: add v0.2.9 changelog
```

## Architecture

### Project Structure: Single Package

This project uses **type-based** module organization.

### Source Layout

```
src/
├── main/
├── test/
```

### Configuration Files

- `.github/workflows/build.yml`
- `ai-bridge/package.json`
- `webview/package.json`
- `webview/tsconfig.json`
- `webview/vite.config.ts`
- `webview/vitest.config.ts`

### Guidelines

- Group code by type (components, services, utils)
- Keep related functionality in the same type folder
- Avoid circular dependencies between type folders

## Code Style

### Language: Java

### Naming Conventions

| Element | Convention |
|---------|------------|
| Files | PascalCase |
| Functions | camelCase |
| Classes | PascalCase |
| Constants | SCREAMING_SNAKE_CASE |

### Import Style: Relative Imports

### Export Style: Named Exports


*Preferred import style*

```typescript
// Use relative imports
import { Button } from '../components/Button'
import { useAuth } from './hooks/useAuth'
```

*Preferred export style*

```typescript
// Use named exports
export function calculateTotal() { ... }
export const TAX_RATE = 0.1
export interface Order { ... }
```

## Testing

### Test Framework: vitest

### File Pattern: `*.test.ts`

### Test Types

- **Unit tests**: Test individual functions and components in isolation


*Test file structure*

```typescript
import { describe, it, expect } from 'vitest'

describe('MyFunction', () => {
  it('should return expected result', () => {
    const result = myFunction(input)
    expect(result).toBe(expected)
  })
})
```

## Error Handling

### Error Handling Style: Try-Catch Blocks

A **global error handler** catches unhandled errors.


*Standard error handling pattern*

```typescript
try {
  const result = await riskyOperation()
  return result
} catch (error) {
  console.error('Operation failed:', error)
  throw new Error('User-friendly message')
}
```

## Common Workflows

These workflows were detected from analyzing commit patterns.

### Feature Development

Standard feature implementation workflow

**Frequency**: ~8 times per month

**Steps**:
1. Add feature implementation
2. Add tests for feature
3. Update documentation

**Files typically involved**:
- `webview/src/components/settings/codexprovidersection/*`
- `webview/src/components/settings/providerlist/*`
- `webview/src/components/toolblocks/*`
- `**/*.test.*`
- `**/api/**`

**Example commit sequence**:
```
refactor: extract shared command tool names and improve parsing robustness
Merge pull request #553 from z231485/main
Merge pull request #499 from pwang1984/fix/codex-stdio-mcp-server-status-2
```

### Test Driven Development

Test-first development workflow (TDD)

**Frequency**: ~4 times per month

**Steps**:
1. Write failing test
2. Implement code to pass test
3. Refactor if needed

**Files typically involved**:
- `**/*.test.*`
- `**/*.spec.*`
- `src/**/*`

**Example commit sequence**:
```
test: add tests for user validation
feat: implement user validation
```

### Refactoring

Code refactoring and cleanup workflow

**Frequency**: ~8 times per month

**Steps**:
1. Ensure tests pass before refactor
2. Refactor code structure
3. Verify tests still pass

**Files typically involved**:
- `src/**/*`

**Example commit sequence**:
```
refactor: extract shared command tool names and improve parsing robustness
Merge pull request #553 from z231485/main
Merge pull request #499 from pwang1984/fix/codex-stdio-mcp-server-status-2
```

### Release Version Bump And Changelog

Prepares a new release by bumping the version, updating changelogs, and updating documentation/readme files.

**Frequency**: ~2 times per month

**Steps**:
1. Update version number in build.gradle
2. Update CHANGELOG.md with new release notes
3. Update webview/src/version/changelog.ts
4. Update README.md and README.zh-CN.md with new version info
5. Update or add sponsor and logo images if needed

**Files typically involved**:
- `build.gradle`
- `CHANGELOG.md`
- `webview/src/version/changelog.ts`
- `README.md`
- `README.zh-CN.md`
- `SPONSORS.md`
- `docs/images/idea-claude-code-gui-logo.png`

**Example commit sequence**:
```
Update version number in build.gradle
Update CHANGELOG.md with new release notes
Update webview/src/version/changelog.ts
Update README.md and README.zh-CN.md with new version info
Update or add sponsor and logo images if needed
```

### Feature Release Merge

Merges a feature branch for a new version, touching a large set of core, frontend, and backend files.

**Frequency**: ~2 times per month

**Steps**:
1. Merge feature branch into main
2. Update core backend Java files
3. Update ai-bridge service files
4. Update webview frontend components and hooks
5. Update i18n locale files
6. Update assets (images/icons)
7. Update changelog and documentation

**Files typically involved**:
- `src/main/java/com/github/claudecodegui/**/*.java`
- `ai-bridge/**/*.js`
- `webview/src/components/**/*.tsx`
- `webview/src/hooks/**/*.ts`
- `webview/src/i18n/locales/*.json`
- `webview/src/assets/images/*`
- `webview/src/version/changelog.ts`
- `CHANGELOG.md`
- `README.md`
- `README.zh-CN.md`

**Example commit sequence**:
```
Merge feature branch into main
Update core backend Java files
Update ai-bridge service files
Update webview frontend components and hooks
Update i18n locale files
Update assets (images/icons)
Update changelog and documentation
```

### Large Module Refactor Split

Splits large monolithic modules into smaller focused files for maintainability, often in both backend (Java) and frontend (TS/JS).

**Frequency**: ~2 times per month

**Steps**:
1. Identify large modules (e.g., Handler.java, App.tsx)
2. Extract related logic into new focused files
3. Update imports and usage throughout the codebase
4. Add or update related tests

**Files typically involved**:
- `src/main/java/com/github/claudecodegui/handler/*.java`
- `src/main/java/com/github/claudecodegui/provider/claude/*.java`
- `webview/src/hooks/*.ts`
- `webview/src/components/**/*.tsx`
- `webview/src/hooks/windowCallbacks/**/*.ts`
- `webview/src/components/settings/hooks/*.ts`

**Example commit sequence**:
```
Identify large modules (e.g., Handler.java, App.tsx)
Extract related logic into new focused files
Update imports and usage throughout the codebase
Add or update related tests
```

### Add Or Update I18n Keys

Adds or updates internationalization (i18n) keys across all supported locale files when introducing new UI features or settings.

**Frequency**: ~2 times per month

**Steps**:
1. Add new keys to webview/src/i18n/locales/en.json
2. Propagate new keys to all other locale files (es.json, fr.json, hi.json, ja.json, ru.json, zh-TW.json, zh.json)
3. Update UI components to use the new i18n keys

**Files typically involved**:
- `webview/src/i18n/locales/en.json`
- `webview/src/i18n/locales/es.json`
- `webview/src/i18n/locales/fr.json`
- `webview/src/i18n/locales/hi.json`
- `webview/src/i18n/locales/ja.json`
- `webview/src/i18n/locales/ru.json`
- `webview/src/i18n/locales/zh-TW.json`
- `webview/src/i18n/locales/zh.json`

**Example commit sequence**:
```
Add new keys to webview/src/i18n/locales/en.json
Propagate new keys to all other locale files (es.json, fr.json, hi.json, ja.json, ru.json, zh-TW.json, zh.json)
Update UI components to use the new i18n keys
```

### Fix Provider Or Model Switch

Fixes issues related to provider or model switching, often involving backend settings and frontend model selection components.

**Frequency**: ~2 times per month

**Steps**:
1. Update backend Java service and settings files to fix provider/model logic
2. Update frontend hooks and components (e.g., useModelProviderState, ModelSelect.tsx)
3. Add or update related tests
4. Update utility modules if model mapping is involved

**Files typically involved**:
- `src/main/java/com/github/claudecodegui/settings/ProviderManager.java`
- `src/main/java/com/github/claudecodegui/CodemossSettingsService.java`
- `src/main/java/com/github/claudecodegui/ClaudeSession.java`
- `webview/src/hooks/useModelProviderState.ts`
- `webview/src/components/ChatInputBox/selectors/ModelSelect.tsx`
- `webview/src/components/ChatInputBox/selectors/ModelSelect.test.tsx`
- `webview/src/utils/claudeModelMapping.ts`
- `webview/src/utils/claudeModelMapping.test.ts`

**Example commit sequence**:
```
Update backend Java service and settings files to fix provider/model logic
Update frontend hooks and components (e.g., useModelProviderState, ModelSelect.tsx)
Add or update related tests
Update utility modules if model mapping is involved
```

### Fix Codex Mcp Server Status

Fixes the Codex MCP server status handling, typically when the status stays on pending.

**Frequency**: ~2 times per month

**Steps**:
1. Update src/main/java/com/github/claudecodegui/settings/CodexMcpServerManager.java to fix status logic
2. Test and verify the fix

**Files typically involved**:
- `src/main/java/com/github/claudecodegui/settings/CodexMcpServerManager.java`

**Example commit sequence**:
```
Update src/main/java/com/github/claudecodegui/settings/CodexMcpServerManager.java to fix status logic
Test and verify the fix
```

### Update Community Section Or Assets

Updates the community section in settings and related assets (e.g., WeChat QR code, GitHub links), including i18n keys.

**Frequency**: ~2 times per month

**Steps**:
1. Update webview/src/components/settings/CommunitySection/index.tsx
2. Update or replace images in webview/src/assets/images/
3. Update i18n locale files for new/changed text
4. Update style files if needed

**Files typically involved**:
- `webview/src/components/settings/CommunitySection/index.tsx`
- `webview/src/assets/images/wxq.png`
- `webview/src/components/settings/CommunitySection/style.module.less`
- `webview/src/i18n/locales/en.json`
- `webview/src/i18n/locales/zh.json`

**Example commit sequence**:
```
Update webview/src/components/settings/CommunitySection/index.tsx
Update or replace images in webview/src/assets/images/
Update i18n locale files for new/changed text
Update style files if needed
```


## Best Practices

Based on analysis of the codebase, follow these practices:

### Do

- Write tests using vitest
- Follow *.test.ts naming pattern
- Use PascalCase for file names
- Prefer named exports

### Don't

- Don't skip tests for new features
- Don't deviate from established patterns without discussion

---

*This skill was auto-generated by [ECC Tools](https://ecc.tools). Review and customize as needed for your team.*
