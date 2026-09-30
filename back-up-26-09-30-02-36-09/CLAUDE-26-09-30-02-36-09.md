# {{PROJECT_NAME}} - Claude Code Instructions

## Project Overview

{{PROJECT_DESCRIPTION}}

This is a multi-type project including:
- **fullstack**
- **desktop**

## Quick Reference - Task Skills

**Frontend Features:**
```
MUST READ:
- skills/vue-nuxt/SKILL.md
- skills/typescript/SKILL.md
```

**Backend Features:**
```
MUST READ:
- skills/fastapi/SKILL.md
- skills/python/SKILL.md
- skills/async-python/SKILL.md
```

**Desktop Features:**
```
MUST READ:
- skills/tauri/SKILL.md
- skills/rust/SKILL.md
- skills/macos-ui-automation/SKILL.md (on macOS)
- skills/windows-ui-automation/SKILL.md (on Windows)
```

## Code Quality Requirements

### Security First
- Never introduce OWASP Top 10 vulnerabilities
- All file operations must respect sandboxing rules
- Credentials must use OS keychain, never plaintext

### Testing Requirements
- Write tests before implementation (TDD)
- Run all tests before committing
- Maintain test coverage above 80%

## Commands

```bash
# Install dependencies
{{INSTALL_COMMAND}}

# Run development
{{DEV_COMMAND}}

# Run tests
{{TEST_COMMAND}}

# Build production
{{BUILD_COMMAND}}
```

## Commit Guidelines

- Use conventional commit format
- Ensure all tests pass before committing
- Never commit sensitive credentials
