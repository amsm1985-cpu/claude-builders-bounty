---
name: generate-changelog
description: Generate a structured Keep-a-Changelog compliant CHANGELOG.md from git history, categorized into Added, Fixed, Changed, and Removed based on Conventional Commits since the last release tag.
---

# Git Changelog Generator Skill

A Claude Code skill and automated CLI tool to inspect git commit history and produce standardized, categorized release notes.

## Invocation

This skill can be invoked natively in Claude Code via:
```text
/generate-changelog
```
or executed directly via Bash:
```bash
bash changelog.sh [OUTPUT_FILE] [RANGE]
```

## Features
- **Git Tag Detection**: Automatically calculates commits between the latest git tag (`git describe --tags --abbrev=0`) and `HEAD`. If unversioned, analyzes initial release history.
- **Auto-Categorization**: Inspects commit subjects against Conventional Commits patterns:
  - `Added`: Features and new functionality (`feat:`, `feat(...):`, `add:`, `added:`, `new:`)
  - `Fixed`: Bug fixes and security patches (`fix:`, `fix(...):`, `bugfix:`, `patch:`, `security:`)
  - `Changed`: Improvements, refactoring, maintenance (`refactor:`, `perf:`, `chore:`, `style:`, `docs:`, `build:`, `ci:`, `test:`, or uncategorized updates)
  - `Removed`: Deletions and deprecations (`remove:`, `removed:`, `revert:`, `deprecate:`)
- **Format Standard**: Strictly follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
- **Robust Parsing**: Uses ASCII unit separators (`0x1f`) to safely handle pipe symbols (`|`), double quotes, and multi-word commit subjects without field corruption.

## Usage Workflow

1. Navigate to your repository root:
   ```bash
   cd /path/to/git-repo
   ```

2. Run the generator:
   ```bash
   bash changelog.sh CHANGELOG.md
   ```

3. Review the generated `CHANGELOG.md`.
