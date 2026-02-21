# Key Important Points: CLAUDE.md Context Files

## The Problem: Context Friction

**Every Claude session starts with ZERO context.**

- LLMs are **stateless** (no memory between sessions)
- You must re-explain: tech stack, directory structure, conventions
- Generic advice instead of project-specific help
- **Productivity killer**

---

## What Is CLAUDE.md?

**A markdown file in your project root that Claude Code automatically loads at session start.**

Think of it as: **Persistent project brief that travels with your code**

```
your-project/
├── CLAUDE.md          ← Auto-loads every session
├── src/
├── tests/
└── package.json
```

---

## How It Works: Stateless LLM + File System

### The Mechanism:

1. **LLM = Stateless** (forgets everything between calls)
2. **File System = Persistent** (your files remain)
3. **CLAUDE.md = Orientation guide** (read first every session)

### Why This Matters:

```
Stateless LLM + File System Access = Persistent state through actual files
```

**Claude reads your project directly** instead of you describing it.

---

## Auto-Loading (Zero Configuration)

When you run `claude` in a directory:

1. Claude Code **automatically detects** CLAUDE.md
2. **Loads it into context** immediately
3. **No manual commands** required

**One-time setup. Automatic benefit forever.**

---

## What Goes In CLAUDE.md: 6 Sections

```markdown
# 1. Project Overview
What does your project do? (1-2 sentences)

# 2. Technology Stack
Languages, frameworks, databases, dependencies

# 3. Directory Structure
```
app/
├── models/
├── routes/
└── tests/
```

# 4. Coding Conventions
Style, naming, patterns your team follows

# 5. Key Commands
- Run: `uvicorn main:app --reload`
- Test: `pytest`
- Migrate: `alembic upgrade head`

# 6. Important Notes
Gotchas, dependencies, security considerations
```

---

## How to Create CLAUDE.md

### Step 1: Ask Claude to Generate It

```bash
claude "Help me create a CLAUDE.md file for this project.
What are the main sections I should include, and can you generate 
a template based on what you see in the codebase?"
```

**Claude analyzes your actual files and proposes structure.**

### Step 2: Review and Refine

- Check if it matches your project
- Add team-specific conventions
- Correct any assumptions

### Step 3: Save the File

Save as `CLAUDE.md` in project root

### Step 4: Verify Auto-Loading

```bash
# Exit Claude
exit

# Start new session
claude

# Test
> What's the tech stack for this project?
```

**If Claude mentions your stack without you repeating it → Success!**

---

## The Three Roles Framework (Co-Learning)

### Stage 1: Your First Draft
You create basic CLAUDE.md

### Stage 2: AI as Teacher
```
> Review my CLAUDE.md. What important sections am I missing?
```
Claude teaches you best practices

### Stage 3: AI as Student
```
> Our team uses custom auth pattern. Update CLAUDE.md to reflect...
```
You teach Claude your team's constraints

### Stage 4: AI as Co-Worker
You iterate together, converging on optimal solution

**Result: Better CLAUDE.md through collaboration**

---

## AGENTS.md: Universal Standard

### What Is It?

**Universal markdown file that works with ALL AI coding tools**

- Created by OpenAI
- Adopted by 60,000+ open source projects
- Now part of **Agentic AI Foundation (AAIF)** under Linux Foundation

### Key Difference:

| File | Purpose | Scope |
|------|---------|-------|
| **CLAUDE.md** | Rich context for Claude Code | Claude-specific |
| **AGENTS.md** | Universal project context | Works everywhere |

### Best Practice: Use Both

```
your-project/
├── CLAUDE.md      # Rich context for Claude Code
├── AGENTS.md      # Universal context for any AI agent
├── src/
└── ...
```

In CLAUDE.md, reference AGENTS.md:

```markdown
# Project Context

See @AGENTS.md for universal project guidelines.

## Claude-Specific Instructions
[Claude Code specific: skills, hooks, MCP configs]
```

---

## What Goes Where?

| Content | AGENTS.md | CLAUDE.md |
|---------|-----------|-----------|
| Project overview | ✅ | Reference @AGENTS.md |
| Tech stack | ✅ | Reference @AGENTS.md |
| Directory structure | ✅ | Reference @AGENTS.md |
| Coding conventions | ✅ | Reference @AGENTS.md |
| Key commands | ✅ | Reference @AGENTS.md |
| Claude-specific skills | ❌ | ✅ |
| MCP server configs | ❌ | ✅ |
| Subagent definitions | ❌ | ✅ |
| Hooks configuration | ❌ | ✅ |

**Simple rule:** Universal context → AGENTS.md, Claude features → CLAUDE.md

---

## Creating Both Files

```bash
claude "Create an AGENTS.md file with universal project context 
that any AI coding agent can understand. Then update my CLAUDE.md 
to reference @AGENTS.md for common context and add Claude-specific 
instructions separately."
```

---

## Troubleshooting

### CLAUDE.md Not Loading?

**Checklist:**
- ✅ File named exactly `CLAUDE.md` (case-sensitive)
- ✅ In project root (same level as `.git`, `package.json`)
- ✅ Restarted Claude Code session (new terminal)
- ✅ File has content (not empty)

**Solution:** Restart terminal completely

### What Should Go In?

**Ask yourself:** "Does Claude need to know this to give good suggestions?"

If Claude would ask "What's your tech stack?" without CLAUDE.md → it belongs in CLAUDE.md

### File Size Concerns?

- Typical CLAUDE.md: **1-3 KB**
- Context is cheap; clarity is expensive
- Well-organized CLAUDE.md saves time every session

---

## Why This Matters: Productivity

**The Principle: "Specify Once, Benefit Always"**

✅ **One-time creation:** 10-15 minutes  
✅ **Automatic benefit:** Every session starts with full context  
✅ **No friction:** No re-explaining  
✅ **Team alignment:** New members read CLAUDE.md to understand project  

---

## Key Benefits

### Before CLAUDE.md:
- ❌ Re-explain project every session
- ❌ Generic advice
- ❌ Context friction
- ❌ Wasted time

### After CLAUDE.md:
- ✅ Auto-loads project context
- ✅ Specific, project-aware suggestions
- ✅ Zero friction
- ✅ Productive from first command

---

## Connection to Other Lessons

**Builds on:**
- Installation (Lesson 2/3)
- Hello Claude (Lesson 4)

**Foundation for:**
- Skills (Lesson 8-9)
- Subagents (Lesson 11, 13)
- MCP (Lesson 12-13)
- Hooks (Lesson 15)

**CLAUDE.md is the foundation for all Claude Code intelligence.**

---

## Example CLAUDE.md Template

```markdown
# Project Overview
A Python FastAPI web application for internal business workflows

# Tech Stack
- Python 3.13
- FastAPI 0.104
- PostgreSQL 15
- SQLAlchemy 2.0

# Directory Structure
app/
├── models/          # SQLAlchemy models
├── routes/          # API endpoints
├── middleware/      # Custom middleware
└── tests/           # Pytest test files
alembic/             # Database migrations

# Coding Conventions
- Type hints required on all functions
- Google-style docstrings
- Custom auth: @require_auth, @require_admin decorators
- All auth logic in middleware/auth.py
- JWT tokens in httpOnly cookies

# Key Commands
- Run app: `uvicorn app.main:app --reload`
- Run tests: `pytest`
- Run migrations: `alembic upgrade head`
- Create migration: `alembic revision --autogenerate -m "description"`

# Important Notes
- Database migrations MUST be reviewed before merge
- All endpoints require authentication except /health
```

---

## Bottom Line

**CLAUDE.md eliminates context friction:**

1. Write it once (10-15 minutes)
2. Auto-loads every session
3. Claude understands your project immediately
4. No more re-explaining
5. Better suggestions, faster results

**Add AGENTS.md for universal compatibility across all AI tools.**