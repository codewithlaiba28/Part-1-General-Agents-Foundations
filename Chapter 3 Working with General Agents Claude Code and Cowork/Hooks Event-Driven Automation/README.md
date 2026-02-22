# Hooks: Key Points

## The Core Problem
Without hooks, you **hope** Claude remembers to format code, run tests, or follow conventions. With hooks, you **guarantee** it happens—your code runs automatically, not Claude choosing to run it.

## What Hooks Do
**Event-driven automation** that runs your commands when Claude does something:

```
Claude edits file → PostToolUse hook runs Prettier
Claude runs bash → PreToolUse hook logs command
You submit prompt → UserPromptSubmit hook injects context
Session starts → SessionStart hook loads environment
```

## Five Main Hook Events

| Event | When It Fires | Common Uses |
|-------|---------------|-------------|
| **PreToolUse** | Before tool runs | Validate commands, block dangerous ops |
| **PostToolUse** | After tool completes | Format code, run tests, log activity |
| **UserPromptSubmit** | When you submit prompt | Add context, inject system info |
| **SessionStart** | Claude Code starts | Load env vars, show project info |
| **SessionEnd** | Session closes | Cleanup, save logs |

## How Hooks Work
```
Event fires → Hook script runs → Script output affects Claude

Exit codes:
0 = Success (process output)
2 = Block action (show error)
Other = Non-blocking warning
```

## Configuration (Two Methods)

**Method 1: Interactive**
```bash
/hooks
→ Select event
→ Add matcher
→ Add command
→ Save
```

**Method 2: Edit `.claude/settings.json`**
```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "bash .claude/hooks/log-command.sh"
          }
        ]
      }
    ]
  }
}
```

## Matcher Patterns
```
"Bash"        → Only Bash tool
"Write|Edit"  → Write OR Edit
"Skill.*"     → All Skill tools
""            → All tools
```

## Simple Example: Log All Bash Commands
```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.command' >> ~/.claude/bash-log.txt"
          }
        ]
      }
    ]
  }
}
```

## Hook Input/Output
**Input (via stdin):**
```json
{
  "session_id": "abc123",
  "tool_name": "Bash",
  "tool_input": {
    "command": "npm test",
    "description": "Run tests"
  }
}
```

**Output (via stdout):**
```bash
echo "Logged at $(date)"
exit 0
```

## Common Use Cases
✅ **Auto-format code** after edits (PostToolUse)
✅ **Block dangerous commands** (PreToolUse with exit 2)
✅ **Load project context** on startup (SessionStart)
✅ **Log all activities** for debugging (any event)
✅ **Inject environment variables** (UserPromptSubmit)

## Critical Understanding
- **Hooks ≠ Skills/MCP** - Hooks automate behavior; Skills/MCP add capabilities
- **Start simple** - Claude Code works fine without hooks; add them when you have repetitive patterns
- **Non-blocking** - Hook errors don't break your session; they're logged for investigation

## Bottom Line
**Turn suggestions into guarantees.** Instead of prompting "remember to format," use PostToolUse hooks to ensure it happens every time—automatically, reliably, invisibly.