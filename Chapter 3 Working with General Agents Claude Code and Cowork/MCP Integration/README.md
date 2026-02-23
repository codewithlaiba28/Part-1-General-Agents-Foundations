# MCP Integration 

## WHAT IS MCP?

**MCP (Model Context Protocol) = Safe, approved access to external systems beyond your computer**

**Without MCP:** Claude sees only local files  
**With MCP:** Claude can browse web, fetch docs, query databases, access APIs

**Analogy:** Phone directory of approved specialists Claude can call when needed

---

## TWO BEGINNER-FRIENDLY SERVERS (MEMORIZE)

### 1. Playwright MCP (Web Browsing)
```bash
claude mcp add --transport stdio playwright npx @playwright/mcp@latest
```
**Use for:** Browse websites, find products, extract information

### 2. Context7 MCP (Documentation)
```bash
claude mcp add --transport stdio context7 npx @upstash/context7-mcp
```
**Use for:** Fetch latest docs, always-current information

**Verify installation:**
```bash
claude mcp list
```

---

## HOW TO USE MCP

### Workflow 1: Browse Amazon (Playwright)
```
Use the Playwright MCP to browse Amazon. 
Find 3 men's casual shirts under $30 with good reviews.
```

**Result:** Links, prices, ratings, sizing notes

### Workflow 2: Fetch Docs (Context7)
```
Use Context7 MCP to fetch the latest documentation 
about MCP support in Claude Code.
```

**Result:** Current summary with citations and links

**Iterate naturally:** "filter to long-sleeve" or "show only Prime-eligible"

---

## SKILLS + MCP COMPLEMENTARITY (CRITICAL)

| Component | Role | Analogy |
|-----------|------|---------|
| **Skills** | The "How-To" — expertise packs | Teaching Claude workflows |
| **MCP** | The "With-What" — data pipes | Connecting to live data |

**Together:** Claude knows HOW (skill) + has access to WHAT (MCP)

**Example:** Skill = financial reporting procedures, MCP = accounting database access → Automated reports with real-time data

---

## MCP TOOL SEARCH (AUTO EFFICIENCY)

**Problem:** Each MCP server adds 3,000-12,000 tokens of tool definitions

**Solution:** MCP Tool Search (built-in since Claude Code 2.1.7+)
- Lazy loads tools on-demand
- Only loads tools you actually use
- ~85% automatic reduction in overhead

**Default:** Auto-activates when tools exceed 10% of context

**Control:**
```bash
ENABLE_TOOL_SEARCH=auto claude        # Default
ENABLE_TOOL_SEARCH=auto:5 claude      # Activate at 5%
ENABLE_TOOL_SEARCH=true claude        # Always on
ENABLE_TOOL_SEARCH=false claude       # Always off
```

**For most users:** Don't configure—works automatically

---

## WHEN TO USE MCP ✅

- **Current information** (docs change frequently)
- **Real-time data** (stock prices, database queries)
- **Web interaction** (browsing, testing, scraping)
- **Safe external integration** (trusted APIs)

**Example:** Financial dashboard with database MCP for real-time trading data

---

## WHEN NOT TO USE MCP ❌

**Private/Sensitive Data:**
- ❌ Company financial records, SSH credentials
- ✅ Use local files + environment variables instead

**High-Frequency Queries:**
- ❌ 1000 queries/second (MCP adds latency)
- ✅ ~10 queries/minute appropriate

**Untrusted Servers:**
- ❌ Random npm packages
- ✅ Only: Anthropic official, modelcontextprotocol.io, verified packages

**Before Understanding Basics:**
- ❌ Build custom MCP servers immediately
- ✅ Master Playwright/Context7 first

---

## SECURITY ESSENTIALS (CRITICAL)

**Stay safe:**
- Use **trusted MCP servers only**
- Tokens/secrets stored in **system keychain** (not plain text)
- Never paste secrets in files—use **environment variables**
- Read source code before installing unknown servers

**Verification checklist:**
- Check GitHub source
- Verify maintainer reputation
- Check recent commits

---

## THE THREE PILLARS (ARCHITECTURE)

```
CLAUDE.md  → Claude knows YOUR PROJECT (context)
    ↓
Skills     → Claude knows YOUR PROCEDURES (expertise)
    ↓
MCP        → Claude knows THE WORLD'S TOOLS (access)
    ↓
Result: Digital FTE (autonomous AI agent)
```

**Without CLAUDE.md:** Generic  
**Without Skills:** Repetitive  
**Without MCP:** Blind to external world  
**With all three:** Truly autonomous

**Thesis:** Context + Procedures + Access = Digital FTE

---

## WHAT MCP UNLOCKS (BEFORE/AFTER)

| Task | Without MCP | With MCP |
|------|-------------|----------|
| Browse Amazon | Can't—you do it manually | Playwright: Claude navigates, extracts, summarizes |
| Check React docs | Uses outdated training data | Context7: Fetches current docs with citations |
| Query database | Can't—you run queries, paste | Database MCP: Claude executes safely |
| Post to Slack | Can't—you copy-paste | Slack MCP: Claude sends messages |
| Analyze GitHub repo | Can't—you clone locally | GitHub MCP: Claude clones, analyzes |

**Pattern:** Without MCP = you're the bottleneck. With MCP = Claude is autonomous partner.

---

## COMMON COMMANDS (QUICK REFERENCE)

**Add server:**
```bash
claude mcp add --transport stdio [name] npx [package]
```

**List servers:**
```bash
claude mcp list
```

**Update all:**
```bash
claude mcp update --all
```

**Use in prompts:**
```
Use the [MCP name] to [task]
```

---

## COMMON MISTAKES

❌ Expecting web access without installing MCP server  
❌ Using untrusted servers (security risk)  
❌ Pasting secrets in files (use environment variables)  
❌ Forgetting web content changes (Claude adapts navigation)  
❌ Building custom servers before mastering basics

---

## CONNECTIONS TO OTHER LESSONS

**Builds on:**
- Lesson 5: CLAUDE.md (local project context)
- Lesson 9: Skills (procedures/expertise)

**This lesson (12):**
- MCP (external system access)

**Leads to:**
- Lesson 13: Compiling MCP to Skills (98% reduction)
- Advanced: Custom MCP servers, database integration

---

## BOTTOM LINE

**MCP = External access through safe, standardized connections**

**Two beginner servers:** Playwright (web) + Context7 (docs)

**Installation:** `claude mcp add --transport stdio [name] npx [package]`

**Complementarity:** Skills = HOW, MCP = WITH WHAT

**Auto efficiency:** MCP Tool Search (85% reduction, built-in)

**Security:** Use trusted sources only, environment variables for secrets

**Three Pillars:** CLAUDE.md (context) + Skills (procedures) + MCP (access) = Digital FTE

**Pattern:** Without MCP = bottleneck. With MCP = autonomous partner.