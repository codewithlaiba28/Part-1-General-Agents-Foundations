# Settings Hierarchy: Key Points

## The Core System
**Three-level configuration** where specificity wins:

```
LOCAL (.claude/settings.local.json)     ← Highest priority
  ↓ overrides
PROJECT (.claude/settings.json)         ← Team shared
  ↓ overrides  
USER (~/.claude/settings.json)          ← Global fallback
```

## What Each Level Does

**User (~/.claude/settings.json)**
- Your personal defaults across ALL projects
- Follows you everywhere on your machine
- Example: preferred model, output style, coding preferences

**Project (.claude/settings.json)**
- Team-agreed standards for THIS project
- Committed to git, shared with team
- Example: security rules, environment configs, permission modes

**Local (.claude/settings.local.json)**
- Your private experiments in THIS project
- Added to .gitignore, never committed
- Example: temporary testing, workflow experiments

## Precedence Rule
**Most specific wins:** Local > Project > User

Example:
```json
User:    { "outputStyle": "Concise" }
Project: { "outputStyle": "Explanatory" }
Local:   { "outputStyle": "Verbose" }

Active: "Verbose" (local overrides all)
```

## Why This Matters
Without hierarchy:
- ❌ Rigid standards (no personal customization) OR
- ❌ Chaos (everyone's setup different)

With hierarchy:
- ✅ Team consistency + personal flexibility
- ✅ Safe experimentation without breaking team standards
- ✅ Temporary overrides without permanent changes

## Critical Rules
1. **Don't delete .claude/ directory** - Contains project configuration
2. **Commit project settings** - Share team standards via git
3. **Gitignore local settings** - Keep experiments private
4. **Use right level for right purpose** - Personal → user, Team → project, Experiments → local

## Bottom Line
Configuration hierarchy = organizational intelligence. Choose the right level for each setting type—user for you, project for team, local for testing. Specificity always wins.