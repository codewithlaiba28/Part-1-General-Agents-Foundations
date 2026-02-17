**Passive AI (2023)**
- Just chat interface
- Text responses only

**Agentic AI (2025+)**
- Autonomous agent that takes actions
- Accesses: files, terminal, browser, APIs
- Executes commands (git, npm, pytest)
- Uses MCP (Model Context Protocol) to connect tools
- OODA Loop: Observe → Orient → Decide → Act
- Works like a digital employee
- Completes multi-step tasks independently

**Main Difference:**
- Passive = answers questions
- Agentic = does the work

**Key Points:**

**The Problem:**
- Chat Interface = WALL blocks AI from codebase
- "Blind Prediction" - can't see/access files

**The Solution:**
- Claude Code = Direct Read/Write Access
- Bridge connects AI to codebase

**Impact Stats:**
- **90%** of Claude Code's own codebase written by Claude Code
- **20% → 80%** internal usage jump at Anthropic (Nov '24 - May '25)
- **5 PRs/day** average engineer output (vs typical 1-2)

**Main Insight:**
"AI didn't need to get smarter; it needed access"

**What Access Enables:**
- Explores codebase naturally
- Follows imports
- Understands project structure
- No instruction needed

**Bottom Line:** Capabilities existed, just needed permission to use them


**Key Points:**

**Passive AI (Chat)**
- Role: Consultant on phone
- Visibility: Blind to screen
- Action: Predicts next word
- Flow: Single-shot response
- Friction: HIGH (copy-paste)

**Agentic AI (Claude Code)**
- Role: Pair programmer
- Visibility: Sees filesystem
- Action: Reasons & Acts
- Flow: Iterative loop
- Friction: LOW (direct edit)

**The OODA Loop:**
1. **Observe** - Read error/file
2. **Orient** - Identify root cause
3. **Decide** - Formulate edit plan
4. **Act** - Execute command
(Then repeat)

**Core Principle:**
**"Friction Removal > Feature Addition"**

**Main Difference:**
- Passive = predicts what to say
- Agentic = reasons what to do, then does it

**Why It Matters:**
Removing friction (direct access) more powerful than adding features

**Key Points:**

**The Problem:**
- Stateless LLM = forgets everything between sessions
- RESET button wipes all context

**The Solution: CLAUDE.md**
- Filesystem = External Memory
- Auto-loads at session start
- Persistent project brief

**What CLAUDE.md Contains:**
1. **Overview** - Problem definition & scope
2. **Stack** - Python 3.13, FastAPI, PostgreSQL
3. **Structure** - src/ for code, tests/ for pytest
4. **Conventions** - Type hints, Google-style docstrings
5. **Commands** - uvicorn main:app --reload
6. **Notes** - Security: Never commit .env

**Benefits:**
- AI remembers project context
- No need to re-explain every session
- Consistent coding standards
- Quick onboarding

**Standardization:**
- Use "AGENTS.md" for universal compatibility
- Use "CLAUDE.md" for Claude-specific features

**Bottom Line:** 
Turn filesystem into AI's memory - write it once, AI remembers forever


**Key Points:**

**What are Skills?**
- SKILL.md files that encode expertise/procedures
- Stored in: `root/.claude/skills/`
- Examples: internal-comms, legal-review

**The Problem:**
- AI output = random (non-deterministic)
- Inconsistent tone and style

**The Solution:**
- Skills constrain AI output
- Enforce specific boundaries, tone, procedures

**Example - Before & After:**

**Without Skill:**
"Here is the announcement. Meeting at 5pm."

**With `internal-comms` Skill:**
"Hey team 👋 Quick reminder for our sync at 5pm. See you there? 👀"

**How It Works:**
- Define procedures in SKILL.md
- AI follows those procedures automatically
- Consistent output every time

**Bottom Line:**
Skills = Teaching AI your company's specific way of doing things through reusable procedure files


**Key Points:**

**What is MCP?**
- Model Context Protocol
- "Phone Book" for Tools
- Connects Claude to external services

**MCP Connections (Hub & Spoke):**
- **Playwright** - Web Access (Browsing)
- **PostgreSQL** - Data (SQL)
- **Context7** - Documentation (Docs)
- **Google Drive** - Files (Storage)

**Safety:**
- Access controlled via allow-lists
- Secrets stored in environment variables
- Never plain text

**The Formula:**

**Context (CLAUDE.md)** 
+
**Procedures (Skills)** 
+
**Access (MCP)** 
= 
**Autonomous Agent**

**Bottom Line:**
MCP = standardized way for AI to connect to any tool/service, turning it from isolated assistant into connected agent with real-world access

**Key Points:**

**Main Agent (Controller)**
- Delegates tasks to specialized subagents

**Three Subagents:**

1. **Explore Agent (Haiku)**
   - Infer: Medium
   - Scans files, maps structure

2. **Plan Agent (Sonnet)**
   - Infer: Medium
   - Creates implementation strategy

3. **Builder Agent**
   - Infer: Medium
   - Executes code changes

**Parallel Orchestration:**
- Explore → Plan → Builder
- Run in sequence or parallel
- Each has isolated context

**Core Principle:**
"Don't ask one AI to do everything"

**Benefits:**
- Specialized subagents = better results
- Isolated context windows = prevent hallucination
- Reduces clutter
- Each agent focused on one task

**Bottom Line:**
Break complex tasks into specialized roles - like a team where each member has one clear job


**Key Points:**

**What are Hooks?**
- Event-Driven Automation
- Programming the Agent's Environment
- Flow: Event Trigger → Hook Script → Execution

**Three Types:**

1. **PreToolUse (Safety)**
   - Trigger: Agent tries to edit `.env`
   - Action: Block operation & Warn user

2. **PostToolUse (Quality)**
   - Trigger: File saved
   - Action: Run `prettier` auto-format

3. **SessionStart (Context)**
   - Trigger: Launching Claude
   - Action: Ingest project logs

**Core Principle:**
"Turn 'Please format this' into a hard system rule"

**Benefits:**
- Automate repetitive tasks
- Enforce safety rules automatically
- Ensure quality standards
- No manual intervention needed

**Bottom Line:**
Instead of asking AI to do something every time, create hooks that automatically trigger actions based on events


**Key Points:**

**The Ralph Wiggum Loop:**
- Self-Healing Workflows & Iteration

**The Loop Process:**
1. **Agent Attempt** → Try task
2. **Check Completion Promise** → Verify success
3. **Criteria Met?** (e.g., 0 Errors)
   - Yes → Success/Exit
   - No → Re-inject & Retry
4. **STOP Hook** - Manual intercept option

**Problem It Solves: Iteration Fatigue**

**Manual Process:**
Run → Error → Copy/Paste → Fix (repeat)

**Autonomous Process:**
Agent tries, fails, learns, retries until success

**Criteria for Use:**
Must be:
- **Objective** - Clear pass/fail
- **Verifiable** - Can be checked
- **Deterministic** - Same input = same output

**Examples:**
- 0 Errors
- Linting passes
- Tests pass
- Upgrades complete
- JetBrains Mono (example use case)

**Bottom Line:**
Agent keeps retrying automatically until it meets success criteria - eliminates manual copy/paste/retry cycles


**Key Points:**

**The Creator's Workflow (Boris Cherny)**
Orchestration in Practice

**1. Parallel Sessions**
- Treat Claude as capacity to schedule
- Run 15-20 tabs simultaneously

**2. Plan Mode First**
- Align on the plan before execution
- Wrong fast answer costs more than right slow one

**3. Verification Loops**
- Trust but Verify
- Use hooks and browser tools to force self-checking

**4. Living Context**
- Every mistake updates `CLAUDE.md`
- Build institutional memory

**Core Principles:**
- Scale with parallelization
- Plan before acting
- Automate verification
- Learn from every error

**Bottom Line:**
Treat AI like a scalable workforce - run multiple tasks in parallel, plan first, verify automatically, and continuously improve the system through documented learnings

**Key Points:**

**The Second Pivot: Claude Cowork**
Agentic Power for Knowledge Workers

**Claude Code vs Claude Cowork:**

**Claude Code:**
- User: Developers
- Focus: Git, Tests, Builds
- Interface: CLI / Terminal

**Claude Cowork:**
- User: Knowledge Workers
- Focus: Docs, Spreadsheets, Organization
- Interface: Desktop GUI

**Shared Foundation:**
- Claude Agent SDK
- Skills transfer seamlessly between both

**Bottom Line:**
Same agentic AI technology, different interfaces:
- Cowork = bringing agent capabilities from developers to non-technical knowledge workers
- Same skills, different audience

**Key Points:**

**Cowork in Action: From Chat to Execution**

**Three Use Cases:**

**1. Organization**
- Prompt: "Clean up Downloads folder"
- Action: Organizes by file type, deletes old installers

**2. Synthesis**
- Prompt: "Read 20 PDFs and extract themes"
- Action: Multi-document analysis and summary generation

**3. Batch Processing**
- Prompt: "Convert & compress 50 videos"
- Action: Batch file operations

**Connectors: MCP for Everyone**
- Google Drive
- Slack
- Notion
- GitHub
- Zero-code integrations for everyday tools

**Bottom Line:**
Cowork = turning everyday file/data tasks into automated workflows through simple prompts, with native integrations to common productivity tools


**Key Points:**

**The Office Suite**
Built-in Capabilities for Standard Formats

**DOCX (Word)**
- Tracked Changes
- Formatting
- Preservation
- Header/Footer Management

**XLSX (Excel)**
- Formula Awareness
- Data Analysis
- Chart Generation

**PPTX (PowerPoint)**
- Slide Creation from Outline
- Theme Application
- Layout Management

**PDF**
- OCR Extraction
- Structure Analysis
- Table Identification

**Critical Difference:**
"Native manipulations, not text approximations"

**Bottom Line:**
Cowork doesn't just read/write files as text - it understands and manipulates the actual file formats with full feature support (formulas, formatting, layouts, etc.)


**Key Points:**

**The Business Model: Digital FTEs**
Selling Outcomes, Not Time

**Economics Comparison:**

**Human Employee:**
- $5k/mo
- 40 hrs/week
- Slow Ramp

**Digital FTE:**
- $500/mo
- 168 hrs/week (24/7)
- Instant Scale

**4 Revenue Models:**

1. **Subscription**
   - Hosted Agent (e.g., Contract Reviewer)

2. **Success Fee**
   - Pay-per-result (e.g., $5/lead)

3. **Licensing**
   - Sell the SKILL.md (Enterprise)

4. **Marketplace**
   - Volume sales (App Stores)

**Core Concept:**
Moving from 'Tool User' to 'IP Creator'

**Bottom Line:**
Digital agents work 4x more hours at 1/10th the cost with instant scalability - monetize through outcomes (results) rather than hourly billing


**Key Points:**

**The Agent Factory: The Future of Work**

**Formula for Digital FTE:**

**Context (CLAUDE.md)** 
+ 
**Procedures (Skills)** 
+ 
**Access (MCP)** 
= 
**Digital FTE**

**Evolution of Work:**

1. **Manual Operator** - Doing everything yourself
2. **Assisted User** - AI helps you
3. **Agentic Orchestrator** - You manage AI agents
4. **Agent Factory Owner** - You own agent infrastructure

**Core Principle:**
"Stop building agents from scratch. Build Skills instead."

**Bottom Line:**
The future = owning reusable Skills (procedures) that can be combined with any context and access to create infinite specialized agents - shifting from one-off agent building to scalable agent production

