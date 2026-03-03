# EXAM KEY POINTS: Subagents and Orchestration (SHORT VERSION)

## WHAT ARE SUBAGENTS?

**Subagent = Specialized AI assistant with isolated context window**

**One task, one completion:** Receives goal → Works independently → Returns results → Control back to main Claude Code

**Think:** Project manager (Claude Code) + team of specialists (subagents)

---

## BUILT-IN AGENTS (MEMORIZE)

| Agent | Best For | Model |
|-------|----------|-------|
| **Explore** | Find files, search code, understand structure | Haiku (fast) |
| **Plan** | Complex multi-step tasks, implementation strategies | Sonnet (smart) |
| **general-purpose** | Multi-step tasks with various tools | Sonnet |
| **Bash** | Command execution | Inherits current |
| **claude-code-guide** | Questions about Claude Code | Haiku |

**View agents:** `/agents`

---

## HOW THEY WORK (CRITICAL FLOW)

```
You 
→ Main Claude Code (recognizes task) 
→ Launches Subagent (isolated context) 
→ Subagent completes work 
→ Returns results 
→ Main Claude Code 
→ You continue
```

**Key:** Each subagent starts fresh, no clutter from other tasks

---

## ACTIVATION MODES

### Automatic (Claude decides):
```
"What files handle authentication?" 
→ Explore auto-activates
```

### Explicit (You specify):
```
Use the Plan subagent to analyze this feature request
```

---

## WHY CONTEXT ISOLATION MATTERS

**Without subagents:**
- One AI does everything
- Context fills with mixed information
- Confusion between tasks

**With subagents:**
- Each specialist has clean focus
- No cross-task contamination
- Higher quality results

**Analogy:** Team meeting where researcher presents, then leaves. Strategist creates plan with fresh focus.

---

## PARALLEL EXECUTION (POWERFUL)

**Multiple subagents in one prompt:**

```
Use Explore to show me what files are in this project, 
AND use Plan to outline how I could add a README
```

**Result:** Both work in parallel, results combine

---

## CREATE CUSTOM SUBAGENT (4 STEPS)

### Step 1: Open Menu
```
/agents → "Create new agent"
```

### Step 2: Choose Location
- **Project:** `.claude/agents/` (this project only)
- **Personal:** `~/.claude/agents/` (all projects)

### Step 3: Method
- **Generate with Claude** (recommended)
- Manual configuration

### Step 4: Describe
```
"Help me review code for bugs and suggest improvements.
Use when I say 'review this code' or 'check for bugs'."
```

**Claude generates:** Name, instructions, tool permissions

---

## SUBAGENT FILE STRUCTURE

**Example:** `.claude/agents/code-reviewer.md`

```yaml
---
name: code-reviewer
description: Reviews code for bugs and suggests improvements
model: sonnet
---

# Instructions

When reviewing code:
1. Check for bugs and edge cases
2. Suggest performance improvements
3. Note security concerns
4. Recommend cleaner patterns
```

---

## SUBAGENT IDEAS (COMMON USE CASES)

- **Research:** Documentation deep-dive, requirements gathering
- **Testing:** Generate test cases, identify edge cases
- **Documentation:** README, API docs, architecture notes
- **Refactor:** Code patterns, reduce complexity
- **Code Review:** Bugs, improvements, security

**Pattern:** What expertise? What should it do? What format for results?

---

## COMMON MISTAKES

❌ Expecting subagents to remember previous work  
❌ Trying to continue dialogue after subagent completes  
❌ Using subagents for simple tasks  
❌ Creating broad subagents (defeats isolation purpose)

---

## CRITICAL DISTINCTIONS

**Subagent vs Skill:**

| Feature | Subagent | Skill |
|---------|----------|-------|
| What | Isolated AI specialist | Reusable instructions |
| Context | Own isolated window | Shares main context |
| When | Complex/multi-step tasks | Repeated patterns |
| Invocation | Explicit or auto-delegate | Auto-triggers on description match |

---

## HANDS-ON COMMANDS

**View agents:**
```
/agents
```

**Use subagent explicitly:**
```
Use the Explore subagent to tell me what's in this folder
```

**Parallel execution:**
```
Use Explore to find X, AND use Plan to suggest Y
```

**Create new:**
```
/agents → Create new agent → Describe purpose
```

---

## THE HIERARCHY (3 TIERS)

```
Claude Code (Orchestrator)
    ↓
Subagents (Specialized agents)
    ↓
Skills (Reusable capabilities)
```

**Claude Code coordinates → Subagents execute → Skills provide expertise**

---

## CONNECTIONS TO OTHER LESSONS

**Builds on:**
- CLAUDE.md (project context)
- Skills (reusable expertise)

**This lesson (11):**
- Subagents (delegation with isolation)

**Leads to:**
- Lesson 12: MCP (external system integration)
- Chapter 4, Lesson 9: Agent Teams (multi-agent collaboration)

---

## BOTTOM LINE

**Subagents = Specialists with isolated context**

**Flow:** One task → Complete → Return → Control back

**Built-in agents:** Explore, Plan, general-purpose, Bash, claude-code-guide

**Create custom:** `/agents` → Generate with Claude

**Power:** Parallel execution, clean context, focused results

**When to use:** Complex tasks, need isolation, repeated specialist work