# MCP to Skills: Key Points

## The Core Problem
- **MCP servers load ALL tools upfront** → 5,000-8,000 tokens per server
- Agent with 1,000 tools = **150,000 tokens before your first request**
- Repeated use multiplies waste (use 3x = 15,000-24,000 tokens)

## The Solution: Compiled Skills
**97-99% token reduction** by moving execution outside Claude's context:

```
Direct MCP:          ~15,000-24,000 tokens
Compiled Skill:      ~150-250 tokens
Savings:             98%+
```

## How It Works
1. **SKILL.md** (~150 tokens) - loaded once
2. **Local scripts** execute via bash (0 tokens in context)
3. **Only filtered results** return to Claude

```
browsing-with-playwright/
├── SKILL.md           # Procedures (~150 tokens)
├── scripts/
│   ├── mcp-client.py  # Runs outside context
│   └── start-server.sh
```

## Two Example Skills (Skills Lab)
1. **browsing-with-playwright** - Browser automation
2. **fetch-library-docs** - Documentation with content filtering

## When to Compile
✅ **Use compiled skill:**
- High token servers (5,000+ tokens)
- Frequent use (3+ times)
- Need local filtering (1,000 items → 20 results)
- Multi-step workflows
- Team sharing

❌ **Use direct MCP:**
- One-off queries
- Low overhead (<1,500 tokens)
- Small, simple results

## Smart Skills Pattern
Skills can guide Claude on *when* to use themselves vs Tool Search:
- Simple task → "Use Tool Search"
- Complex/filtering → "Use compiled scripts"

## Bottom Line
**Progressive disclosure:** Load only what's needed, execute heavy operations locally, return only filtered results. Same functionality, 98% fewer tokens.