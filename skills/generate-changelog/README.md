# Git Changelog Generator

A zero-dependency bash tool and native Claude Code agent skill that generates structured, [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) compliant release notes directly from git history.

## 🚀 Setup Instructions (3 Steps)

1. **Make Executable**:
   ```bash
   chmod +x changelog.sh
   ```

2. **Run in any Git Repository**:
   ```bash
   bash changelog.sh CHANGELOG.md
   ```

3. **Check the Output**:
   Open `CHANGELOG.md` to see commits since the last release tag automatically categorized into `Added`, `Fixed`, `Changed`, and `Removed`.

---

## 💡 Claude Code Skill Integration

You can also run this skill directly inside Claude Code:
```text
/generate-changelog
```

## 📋 Categorization Rules

| Category | Trigger Prefixes | Example |
|---|---|---|
| **Added** | `feat:`, `feat(...):`, `add:`, `added:`, `new:` | `feat(auth): add OAuth2 provider` |
| **Fixed** | `fix:`, `fix(...):`, `bugfix:`, `patch:`, `security:` | `fix(api): prevent null pointer exception` |
| **Changed** | `refactor:`, `perf:`, `chore:`, `style:`, `docs:`, `build:`, `ci:`, `test:` | `refactor(db): optimize connection pooling` |
| **Removed** | `remove:`, `removed:`, `revert:`, `deprecate:` | `remove: drop deprecated v1 endpoints` |

## 🧪 Acceptance Criteria Verified
- ✅ Executable via `/generate-changelog` or `bash changelog.sh`
- ✅ Automatically queries commits since the last tag (`git describe --tags --abbrev=0`)
- ✅ Strict Keep-a-Changelog structure
- ✅ Unit-separator-safe parser (handles pipes `|`, quotes, and complex characters)
- ✅ Setup in 3 steps or fewer
