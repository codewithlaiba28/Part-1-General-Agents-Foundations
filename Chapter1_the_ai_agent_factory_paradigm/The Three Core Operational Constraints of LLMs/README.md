# The Three Core Operational Constraints of LLMs

1. **Statelessness** - LLMs have no memory between conversations; every interaction starts fresh unless you explicitly provide context

2. **Context Window Limits** - There's a finite amount of information an LLM can consider at once (measured in tokens)

3. **Non-Determinism** - Same prompt can produce different outputs; LLMs are probabilistic, not deterministic systems

**Implication**: All AI development methodologies (Spec-Driven Development, context engineering, OODA loops) exist specifically to work *with* these constraints, not against them.

# Constraint 1: LLMs Are Stateless

## Core Reality
- **Every interaction = complete amnesia**
- Model has ZERO memory between API calls
- True for all models (Claude, GPT, Gemini)

## The Illusion of Memory
Chat apps **store and re-send** entire conversation history with each message:
```
Message 1: "My name is Maya"
Message 2: "What's my name?" 
→ App sends: [Message 1 + Message 2] to model
→ Model reads from scratch, answers, forgets
```

## Critical Implications

1. **Context must be explicitly provided every time**
   - Why AGENTS.md exists: persistent context file

2. **Specifications are essential, not optional**
   - It's the only info the model will ever have

3. **Continuity is an application layer feature**
   - Tools like Claude Code inject context repeatedly

4. **Long projects need explicit state management**
   - SPEC.md, PROJECT_CONTEXT.md = your memory system

## What This Means Practically

| Wrong Expectation | Reality | Solution |
|---|---|---|
| "Remembers my style" | No memory | Style guide in AGENTS.md |
| "Knows my project" | Starts fresh | Give access to codebase |
| "Learned from last chat" | No learning | Document decisions |
| "Will remember preference" | Forgotten instantly | Config files |

**Bottom line**: The model forgets everything. Your job is to build the memory system.


# Constraint 2: LLMs Are Probabilistic, Not Deterministic

## Core Reality
- **Same input ≠ same output**
- Models sample from probability distributions
- Randomness is fundamental, not a bug
- True for all models (Claude, GPT, Gemini)

## How It Works
```
Prompt: "Best language for web dev is"

Run 1: "JavaScript, because..."
Run 2: "TypeScript, given..."  
Run 3: "Python with Django..."

All valid. All different. Working as designed.
```

## Temperature Parameter

| Setting | Behavior | Use Case |
|---------|----------|----------|
| 0 | Most deterministic (picks highest probability) | Repetitive but consistent |
| 0.7 | Balanced (default) | Creative yet coherent |
| 1.0+ | High creativity | Risk of incoherence |

*Even at temp=0, subtle variations occur*

## Critical Implications

1. **Identical prompts → different code**
   - Not a bug; it's how it works

2. **Validation is mandatory**
   - Why SDD has a "Validate" phase

3. **Specs constrain variation**
   - Vague prompt = wild variation
   - Precise spec = bounded variation

4. **TDD becomes critical**
   - Tests = deterministic requirements for probabilistic outputs

5. **Iteration is standard workflow**
   - Plan for 1-2 refinement cycles always

## Practical Reality Check

| Wrong Expectation | Reality | Solution |
|---|---|---|
| Same prompt = same code | Different every time | Use specs + validation |
| "It gave me X last time" | No consistency guarantee | Version control what works |
| "Fix bug" = same fix | Multiple valid fixes | Review + test each |
| Reproducible test generation | Different tests each run | Define coverage explicitly |

## The Upside

This is also a **strength**:
- ✓ Creative problem-solving
- ✓ Multiple valid solutions to compare
- ✓ Exploration of solution space

**Bottom line**: Stop expecting determinism. Build validation instead.


# Constraint 3: Context Is Limited, Not Infinite

## Core Reality
- **Fixed "context window" = working memory**
- Stores EVERYTHING: system prompt + history + files + response
- Once full, older content gets truncated

## Context Window Sizes (Early 2026)

| Model | Context Window | Equivalent |
|-------|---------------|------------|
| GPT-5.2 | 256K tokens | ~600 pages |
| Claude Opus 4.5 | 200K tokens | ~500 pages |
| Gemini 3 Pro | 2M tokens | ~5,000 pages |

**Tradeoffs of larger windows**: Higher latency, higher cost, "lost in the middle" effect

## What Fills Context Fast

```
System prompt (AGENTS.md, skills):     5K-20K tokens
Specification:                         1K-5K tokens
Conversation history:                  2K-50K tokens
Code files:                           10K-100K tokens
Model response:                        1K-10K tokens
─────────────────────────────────────────────────────
TOTAL: Exceeds limit quickly on complex projects
```

## Consequences

1. **Information gets lost** - Early messages truncated in long conversations
2. **Large codebases don't fit** - 50K-500K+ lines exceed any window
3. **Context is zero-sum** - History tokens steal from code/spec tokens

## Critical Implications

1. **Context engineering = core skill**
   - What to include/exclude directly impacts quality

2. **AI-First IDEs solve this**
   - Cursor/Windsurf intelligently select relevant code
   - Not just dumping everything

3. **Specs compress intent**
   - "10 criteria" > 50-message discovery conversation

4. **Project structure matters**
   - Small, well-named files > monolithic files
   - Easier selective inclusion

5. **Conversation management is strategy**
   - Reset long debugging sessions with fresh context

## Practical Reality Check

| Wrong Expectation | Reality | Solution |
|---|---|---|
| "Sees whole codebase" | Only selected files fit | AI-First IDEs with smart selection |
| "Remembers full conversation" | Old messages truncated | Focus conversations; start fresh |
| "More context = better" | Noise dilutes signal | Curate carefully; quality > quantity |
| "Knows everything in repo" | Hard context limits | Structure for selective inclusion |

## Context Management Strategies

**Specifications**: Front-load critical requirements (top survives truncation)

**Code**: Reference by path, let AI retrieve (when it has file access)

**Conversations**: Reset when unwieldy:
```
"Let's reset. Building user registration.
Decided: PostgreSQL, bcrypt, AWS SES.
Now need: rate limiting implementation."
```

**Projects**: Maintain PROJECT_CONTEXT.md for state injection

**Bottom line**: Context is your scarcest resource. Manage it strategically.

# How the Three Constraints Interconnect

## The constraints don't exist in isolation—they compound:

### 1. **Stateless + Limited Context**
- Model forgets everything → must re-inject context every session
- But context is limited → must re-inject **efficiently**
- **Why AGENTS.md is concise, not exhaustive**

### 2. **Probabilistic + Stateless**
- Each session starts fresh AND produces variable output
- No guarantee model approaches problem the same way twice
- **Why version control + decision documentation are critical**

### 3. **Probabilistic + Limited Context**
- Constrained context = less info to anchor probabilistic generation
- **Vague spec + limited context = wild variation**
- **Clear spec + limited context = useful variation within bounds**

---

## The Compounding Effect

```
Stateless: "Forgets everything"
    +
Limited Context: "Can't see everything"
    +
Probabilistic: "Won't repeat exactly"
    =
NEED: Efficient, persistent state management
      + Strategic context curation
      + Validation systems
```

**Bottom line**: These constraints work together to demand a fundamentally different development approach. Fight one, you fight all three. Work with all three, and AI becomes reliably productive.


# The Methodological Response

## Every Practice Exists Because of These Constraints

| Constraint | Creates Need For | Addressed By |
|------------|-----------------|--------------|
| **Stateless** | Persistent context that survives sessions | AGENTS.md, SPEC.md, MCP, Skills |
| **Probabilistic** | Validation of variable outputs | SDD's Validate phase, TDD, Quality Gates |
| **Limited Context** | Efficient representation of requirements | Specification-first thinking, Context engineering |

---

## How Spec-Driven Development Addresses All Three

**Statelessness** → Specifications persist across sessions  
**Probabilistic** → Clear specs constrain outputs, reduce variation  
**Limited Context** → Concise specs maximize context window use

---

## How Other Practices Map to Constraints

### **AGENTS.md**
- **Constraint**: Stateless
- **Solution**: Persistent file injected into every session
- **Effect**: Consistent baseline knowledge without re-explaining

### **MCP (Model Context Protocol)**
- **Constraint**: Limited Context
- **Solution**: Dynamic retrieval instead of upfront loading
- **Effect**: Access to info beyond context window

### **Test-Driven Development**
- **Constraint**: Probabilistic
- **Solution**: Define invariants (tests) any valid implementation must satisfy
- **Effect**: Accepts variable outputs while ensuring correctness

### **Context Engineering**
- **Constraint**: Limited Context
- **Solution**: Strategic curation of what enters context window
- **Effect**: Quality over quantity; signal over noise

---

**Bottom line**: These aren't arbitrary best practices. They're engineered responses to fundamental constraints. Understanding the constraints reveals why the methodologies work.


# Key Points: Developer's Mental Model & Practical Application

## **Mental Model Shift**

### Old (Incorrect):
- "AI is a knowledgeable colleague who remembers our work"
- "Explain once, it knows it"
- "Same prompt = same result"

### New (Correct):
- "AI is a **brilliant expert with amnesia** - brief from scratch each time"
- "Must provide all relevant context every session, **concisely**"
- "Specify what I need, **validate what I get**, **expect iteration**"

**This is pragmatic, not pessimistic** - stop fighting constraints, design workflows that work with them

---

## **Critical Risks**

### Hallucination Risk
- LLMs generate **confident but wrong code** (subtle bugs, non-existent APIs, incorrect logic)
- Not lying - probabilistic nature producing from statistical patterns
- **Validation is mandatory** - cannot trust AI code without verification

### Context and Cost
- Every token costs money (charged per input/output)
- Poor context management = **higher costs at scale**
- Efficient specs + context engineering = quality **AND** economics

---

## **Summary Table: The Three Constraints**

| Constraint | What It Means | Your Response |
|------------|---------------|---------------|
| **Stateless** | No memory between sessions; history re-sent each time | Persist context in files (AGENTS.md, specs); design for fresh starts |
| **Probabilistic** | Variable outputs from identical inputs; no reproducibility guarantee | Validate all outputs; use specs to constrain variation; embrace iteration |
| **Limited Context** | Fixed window; all content competes for space | Engineer context carefully; prioritize quality over quantity; use smart tools |

---

## **Try With AI: Hands-On Exercises**

### Exercise 1: Constraint Exploration
Test statelessness, probabilistic nature, and context limits directly - builds **visceral understanding**

### Exercise 2: Context Engineering
Practice minimum context needed, identifying noise, structuring questions - **directly impacts collaboration effectiveness**

---

## **Foundation Complete**
Understanding these constraints is **prerequisite knowledge** - they explain why all methodologies exist and how to apply them effectively. Transforms constraints from limitations into **design parameters**.