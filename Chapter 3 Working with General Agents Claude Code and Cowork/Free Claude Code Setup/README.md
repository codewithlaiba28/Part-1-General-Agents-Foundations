# Free Claude Code Setup - Core Concepts

## Core Concept

Claude Code's CLI is **frontend-agnostic**—it can work with any OpenAI-compatible backend through API routing. This architecture enables a free alternative using Google's Gemini API while maintaining identical Claude Code functionality (subagents, skills, MCP servers, hooks).

---

## Key Mental Models

### Three-Layer Architecture
**CLI (interface) → Router (format translator) → API (AI backend)**

Understanding this separation reveals how tools can be composed beyond vendor lock-in.

### Backend Abstraction
The Claude Code CLI doesn't care what AI responds—it cares about the API format. Routers translate between Anthropic and OpenAI API standards.

### Environment Variables as Secrets
API keys stored in shell config files (`~/.zshrc`, `~/.bashrc`) persist across sessions without hardcoding sensitive data.

---

## Critical Patterns

### Two-Terminal Workflow
Daily workflow requires two terminals:
1. **Terminal 1:** Router starts first → `ccr start`
2. **Terminal 2:** Claude Code connects through it → `ccr code`

### Layer-by-Layer Verification
Verify each layer independently:
- Check Node.js version
- Router configuration
- API key presence

Failures cascade, so **isolate the broken layer**.

### Copy-Paste First, Understand Later
For procedural tasks: **Get it working first, understand the architecture later** (remedial differentiation).

---

## Common Mistakes

❌ **Forgetting to start the router** before launching Claude Code (connection fails silently)

❌ **Hardcoding API keys** directly in config files instead of using environment variables (security risk)

❌ **Using wrong shell config file** (`.zshrc` vs `.bashrc`)—check `echo $SHELL` first

❌ **Expecting router to auto-start** (it's a manual step each session)

---

## Connections

### Alternative to:
Lesson 2's official Claude Max subscription—both paths teach **identical Claude Code skills**

### Leads to:
Lessons 4-13 work identically regardless of which setup path you chose:
- Persistent context
- MCP
- Subagents
- Skills
- Hooks
- Configuration

---

## Quick Reference

```bash
# Check your shell
echo $SHELL

# Start router (Terminal 1)
ccr start

# Launch Claude Code (Terminal 2)
ccr code
```