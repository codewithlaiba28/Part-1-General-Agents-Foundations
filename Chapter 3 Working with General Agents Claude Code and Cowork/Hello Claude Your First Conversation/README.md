# Key Important Points: Hello Claude & CLI Mastery

## Core Concept

**Claude Code is not a chatbot**—it's a **terminal-based agentic environment**. You converse in natural language, but every action requires your explicit approval.

---

## Starting Claude Code

```bash
claude
```

That's it. No special syntax. No commands to memorize.

---

## The Permission Loop (CRITICAL)

Claude **cannot act without your approval**. Every action requires permission:

- ✅ **Read** a file
- ✅ **Write/Create** a file  
- ✅ **Execute** a command

**Approval Controls:**
- Press **[Enter]** to approve
- Press **[Esc]** to reject

**You're never surprised.** Claude can't accidentally delete files or run dangerous commands.

---

## Natural Language Interaction

**No special syntax required.** Just describe what you want:

### Example Workflow:
```
> Search for the latest news about AI agents in 2026 
  and create a file called 'ai-news-2026.txt' with what you find
```

**What happens:**
1. Claude searches the web
2. Claude proposes file with content
3. Prompt appears: `> Create file ai-news-2026.txt?`
4. You press Enter to approve
5. Done.

---

## Slash Commands (Essential CLI Controls)

| Command | Purpose |
|---------|---------|
| `/help` | Show available commands |
| `/clear` | Clear conversation history |
| `/compact` | Reduce token usage |
| `/cost` | Check session cost |

---

## The Cost Pill

**Always monitor session cost** (displayed top right)

Why? Token hygiene = cost control. Use `/cost` to check spending.

---

## Steering (Advanced Control)

You're not limited to yes/no:

❌ **Don't just reject:**
```
> [Esc]
```

✅ **Guide Claude instead:**
```
> No, edit this file instead
> Try a different approach
> Use this format
```

This is **steering**—actively directing Claude's behavior.

---

## First Conversation Pattern

### 1. **Orient Yourself**
```
> Where am I right now?
> What can you do? What are my main options?
```

### 2. **Real Task**
```
> Search for [topic] and save to [filename]
```

### 3. **Approve/Reject**
- Enter = proceed
- Esc = reject and redirect

---

## The Five Extension Tools (Preview)

| If you need... | Then use... | Covered in... |
|----------------|-------------|---------------|
| Persistent context for every session | **CLAUDE.md** | Lessons 5, 7 |
| Repeated procedures done your way | **Skill** | Lessons 8-9 |
| Delegation & focus for complex workflows | **Subagent** | Lessons 11, 13 |
| External systems (APIs, databases) | **MCP** | Lessons 12-13 |
| Automated quality gates & safety | **Hook** | Lesson 15 |

---

## Mental Models to Build

As you continue, recognize these patterns:

- "I need Claude to always format code like this" → **CLAUDE.md**
- "I want Claude to research without interrupting me" → **Subagent**
- "I need Claude to check GitHub before commits" → **Hook**

---

## Connection to Other Lessons

**Builds on:**
- Installation (Lesson 2/3)

**Leads to:**
- CLAUDE.md Context (Lesson 5)
- Practical Problem-Solving (Lesson 6)

---

## Key Safety Reminders

✅ You approve every action  
✅ You can reject and redirect  
✅ Monitor costs with `/cost`  
✅ Start in project directories (not system directories)  
✅ Review all proposed changes  

---

## Practice Exercises

1. **Orientation:**
   ```
   > Where am I? What's in this directory?
   ```

2. **File Creation:**
   ```
   > Search for [topic] and create a summary file
   ```

3. **Test Rejection:**
   ```
   Ask Claude to create a file → Press Esc → Ask for different approach
   ```

---

## Bottom Line

**Claude Code = Natural language + Explicit approval + Steering**

You describe what you want. Claude shows what it will do. You approve or redirect. Simple, safe, powerful.