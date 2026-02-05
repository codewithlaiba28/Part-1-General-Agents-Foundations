# AAIF Standards - The Foundation - Key Points

## **The Problem (Before Dec 9, 2025)**

**Scenario**: You built a Digital SDR that works brilliantly with Claude. Client asks: "Does it work with ChatGPT?"

**Before**: Uncomfortable choice:
- Rebuild for their platform, OR
- Lose the deal

**Issue**: Your expertise (qualification logic, CRM integrations, workflows) was **locked to one vendor**

---

## **The Solution: AAIF**

### **What Is AAIF?**
**Agentic AI Foundation** = Linux Foundation initiative (announced Dec 9, 2025)

**Purpose**: Neutral governance for open standards powering AI agents

**Result**: Digital FTEs are **portable investments**, not platform prisoners

---

## **The Unprecedented Alliance (Dec 9, 2025)**

### Founding Members:
**Donated Core Technologies**:
- **OpenAI**
- **Anthropic** 
- **Block**

**Platinum Members**:
- Amazon Web Services
- Google
- Microsoft
- Bloomberg
- Cloudflare

**Significance**: Fierce competitors came together under neutral governance

---

## **Jim Zemlin (Linux Foundation Executive Director):**

> "We are seeing AI enter a new phase, as conversational systems shift to autonomous agents that can work together. Within just one year, MCP, AGENTS.md and goose have become essential tools for developers building this new class of agentic technologies."

---

## **The Core Insight**

**Infrastructure that everyone needs should belong to everyone**

**Strategy**: 
- Compete on **products** built atop shared foundations
- NOT on the **foundations** themselves

---

## **What Changed**

| Before AAIF | After AAIF |
|-------------|------------|
| Build for one vendor | Build once, run anywhere |
| Platform lock-in | Platform portability |
| Rebuild per client | Reuse across clients |
| Vendor prisoner | Vendor independent |

---

**Bottom line**: AAIF makes AI agent development vendor-neutral, turning proprietary expertise into portable assets


# The USB Lesson: Why Standards Win - Key Points

## **The USB Analogy**

### Before USB Standard:
- Every device had proprietary connectors
- Phone charger ≠ camera charger
- Printer needed special cable
- Switching devices = buying new cables + throwing away old ones

### After USB Standard:
✅ Any USB device works with any USB port  
✅ Manufacturers compete on device quality, not connector lock-in  
✅ Consumers buy with confidence—investment is portable

---

## **AAIF = USB Implementers Forum for AI Agents**

**Just as**:
- USB needed neutral standards body to ensure device ↔ port compatibility

**AAIF ensures**:
- Your Digital FTEs work across any platform
- AAIF **governs** the standards
- The standards **create** the actual portability

---

## **Before vs After Comparison**

| Without Open Standards | With AAIF Standards |
|------------------------|---------------------|
| Rebuild integrations for each AI platform | Write once, deploy everywhere |
| Skills locked to Claude or ChatGPT | Skills work across all major agents |
| Custom code for every client's tools | Universal protocol for tool connectivity |
| Platform vendor lock-in | Switch providers without rebuilding |

---

## **The Economic Logic**

**Standards create larger markets**

**Benefits everyone MORE than fragmented proprietary ecosystems**

- More developers building
- More clients buying
- More innovation on top of shared foundation
- Competition on value, not on lock-in

---

**Bottom line**: Like USB for devices, AAIF standards create portability and interoperability for AI agents—growing the market for everyone


# The Five Standards Foundation - Key Points

## **AAIF Launched With Five Projects**

Complete foundation for portable AI agents

---

## **1. Model Context Protocol (MCP) — From Anthropic**

### **The M×N Problem**

**Before MCP**:
```
Claude → Salesforce:  Custom integration code
ChatGPT → Salesforce: Different custom code
Gemini → Salesforce:  Yet another custom code

Claude → HubSpot:     Another custom integration
ChatGPT → HubSpot:    Another different custom code
```

**3 AI platforms × 2 CRMs = 6 custom integrations**

Add more tools? **Combinations explode**

**M models × N tools = M×N custom integrations**

---

### **What MCP Enables**

**One standard protocol** for all agent-to-tool connections

Write an MCP server **once** → any MCP-compatible agent can use it
- Claude, ChatGPT, Gemini, goose, Custom Agents

**Enables the "Act" power** from Five Powers:
- Without MCP: Agent can reason but **can't execute**
- With MCP: Agent connects to CRM, email, calendars, databases

---

### **Three Universal Primitives**

| Primitive | Purpose | Physical Metaphor | Digital SDR Example |
|-----------|---------|-------------------|---------------------|
| **Resources** | Read-only data | Eyes (see, don't touch) | Lead data from CRM, email history |
| **Tools** | Actions that change state | Hands (make things happen) | Send email, update deal stage, schedule meeting |
| **Prompts** | Reusable templates | Playbooks (standard approaches) | Lead qualification checklist, follow-up email structure |

**Critical**: Getting this wrong breaks your Digital FTE
- Exposing "send email" as Resource = agent can see but **can't send**
- Universal standards prevent universal confusion

---

### **Architecture: Host → Client → Server**

```
┌──────────────────────────────────────┐
│             HOST                      │
│  (Claude Desktop, ChatGPT, your app)  │
│   ┌─────────────────────────────────┐│
│   │          CLIENT                 ││
│   │  (Manages MCP connections)      ││
│   └─────────────┬───────────────────┘│
└─────────────────┼────────────────────┘
                  │ MCP Protocol (JSON-RPC)
┌─────────────────▼────────────────────┐
│             SERVER                    │
│  (Your CRM connector, database, API)  │
│   Resources │ Tools │ Prompts         │
└──────────────────────────────────────┘
```

---

### **Adoption Timeline**

| Date | Milestone |
|------|-----------|
| **Nov 2024** | Anthropic releases MCP as open source |
| **Early 2025** | Block, Apollo, Replit, Zed, Sourcegraph adopt |
| **Mar 2025** | OpenAI officially adopts MCP across products |
| **Apr 2025** | Google DeepMind confirms MCP support for Gemini |
| **Nov 2025** | MCP spec 2025-11-25 with OAuth 2.1, Streamable HTTP |
| **Dec 2025** | MCP donated to AAIF under Linux Foundation governance |

---

### **Mike Krieger (Anthropic CPO):**

> "When we open sourced it in November 2024, we hoped other developers would find it as useful as we did. A year later, it's become the industry standard for connecting AI systems to data and tools."

---

**Bottom line**: MCP solves the M×N integration explosion problem—write once, connect to any agent. Enables the "Act" power that turns reasoning into execution.


# 2. AGENTS.md — From OpenAI - Key Points

## **What It Solves**
- Deploying to 100 clients with different conventions/rules
- **Zero customization needed** per client

## **What It Is**
- Standard Markdown file teaching AI agents local rules
- Agent reads it → understands environment instantly

## **Humans vs Agents**
- **README.md** (humans): What is this project?
- **AGENTS.md** (agents): How should I behave in this project?

## **What Goes In It**
- Build/test commands
- Code style rules
- Security constraints
- File organization patterns

## **The Hierarchy Rule**
- Nearest AGENTS.md takes precedence
- Enables monorepo: different rules per subproject

## **Adoption (Since Aug 2025)**
- 60,000+ open-source projects
- Every major AI coding agent (Claude Code, Cursor, Copilot, Gemini CLI, Devin, goose)
- OpenAI's repo has 88 AGENTS.md files

**Bottom line**: Standard for teaching agents local rules—zero-config deployment


# 3. goose — From Block - Key Points

## **What It Solves**
- MCP = how to connect
- AGENTS.md = how to behave
- **goose** = what a production agent looks like implementing both

## **What It Is**
- **Reference architecture** for building production agents
- Not a demo—**75% of Block engineers save 8-10+ hours/week** with it
- **Apache 2.0 licensed** (study the source code)

## **Why Reference Implementations Matter**
Building Custom Agents? Face questions like:
- How to structure MCP client connections?
- How to handle streaming responses?
- How to manage conversation context?

**Learn from goose** = battle-tested patterns from enterprise use

## **goose in Two Paths Framework**
- **Path A** (General Agents): Ready-to-use like Claude Code, goose
- **Path B** (Custom Agents): Built from SDKs
- **goose** = Path A agent, but open source → **blueprint for Path B**

## **Key Architecture Patterns**

**1. Local-First Execution**
- Code and data stay local
- Enterprise requirement for sensitive IP

**2. MCP-Native Design**
- Add capabilities = connect MCP servers
- No custom integration code
- Every capability follows same pattern

**3. Multi-Model Support**
- Claude, GPT-4, Gemini, Ollama
- Configure different models for different tasks (cheap for simple, premium for complex)

## **goose vs Claude Code**

| Aspect | Claude Code | goose |
|--------|-------------|-------|
| Creator | Anthropic | Block |
| License | Proprietary | **Open Source (Apache 2.0)** |
| MCP Support | Yes | Yes |
| AGENTS.md Support | Yes | Yes |
| Source Code | Closed | **Open** |

**Strategy**: Use Claude Code for productivity today. Study goose for building Custom Agents tomorrow.


# 4. Agent Skills — Packaging Expertise - Key Points

## **The Problem**
- Your expertise (financial analysis, legal review, sales qualification) lives in your head
- Can't scale—you trade time for money
- **You're the bottleneck**

## **What Skills Enable**
Package expertise into portable skills any AI agent can load

**Matrix analogy**: Trinity needs to fly helicopter → Tank loads skill → "Let's go"

Your years of expertise → encoded → loadable by any agent

---

## **The SKILL.md Format**

```markdown
---
name: financial-analysis
description: Analyze financial statements and generate investment reports
---

## When to Use
- Financial statement analysis
- Quarterly earnings interpretation
- Investment comparison

## How to Execute
1. Gather financial documents
2. Extract key metrics
3. Compare against benchmarks
4. Generate structured report

## Output Format
- Executive summary
- Key metrics table
- YoY comparison
- Risk factors
- Recommendation
```

---

## **Progressive Disclosure: Token Efficiency**

**Problem**: Loading all 50 skills upfront = wasted context window

**Solution**: Load only what's needed, when needed

```
Level 1: Startup (~100 tokens/skill)
├── Name + Description only

Level 2: When Activated (<5K tokens)
└── Full SKILL.md content

Level 3: When Actually Needed
└── Supporting resources (templates, examples, scripts)
```

**Result**: **80-98% token reduction** → dozens of capabilities without bloating context

---

## **MCP + Skills: Complementary**

| Standard | Purpose | Physical Metaphor |
|----------|---------|-------------------|
| **MCP** | Connectivity—how agents talk to tools | The agent's **hands** |
| **Skills** | Expertise—what agents know how to do | The agent's **training** |

### Example: Digital SDR Processing Stripe Payments

**MCP Server (Stripe connector)**:
- Connects to Stripe API (create charges, refund, list transactions)

**Skill (Payment processing)**:
- Knows how to handle payment scenarios (retry logic, error recovery, customer communication)

| Scenario | Result |
|----------|--------|
| Without MCP | Agent can't reach Stripe |
| Without Skill | Agent reaches Stripe but doesn't know best practices |
| **With both** | **Agent handles payments like experienced professional** |

---

## **Adoption Timeline**

| Date | Milestone |
|------|-----------|
| **Oct 16, 2025** | Anthropic launches Agent Skills for Claude Code |
| **Dec 18, 2025** | Anthropic releases as open standard at agentskills.io |
| **Dec 2025** | OpenAI adopts same SKILL.md format for Codex CLI and ChatGPT |

**Supported agents**: Claude Code, ChatGPT, Codex CLI, VS Code, GitHub Copilot, Cursor, goose, more

**Partner skills**: Canva, Stripe, Notion, Figma, Atlassian, Cloudflare, Ramp, Sentry, Zapier

---

**Bottom line**: Skills package expertise into portable, token-efficient modules. MCP = hands, Skills = training.


# 5. MCP Apps Extension — Agent Interfaces - Key Points

## **The Problem**
Your Digital SDR works through **chat only**:
- Data visualizations → text descriptions
- Forms → one-question-at-a-time
- Complex tables → formatting puzzles

**Competitor's SDR**: Shows buttons, charts, real-time pipeline views  
**Yours**: Describes them in paragraphs

---

## **What MCP Apps Extension Enables**

**Announced**: Nov 21, 2025 (SEP-1865)

**Capability**: MCP servers deliver **interactive UI** directly to host apps
- Buttons, forms, charts, dashboards—not just chat

---

## **The Evolution**

```
Text Only → Structured Output → Interactive Components
    ↓              ↓                    ↓
  Chat         Markdown/Code      Buttons, Forms,
              Formatting          Visualizations
```

---

## **Architecture**

Uses `ui://` URI scheme with sandboxed iframe security:

```
┌─────────────────────────────────────────────┐
│           MCP Host Application              │
│  ┌─────────────────┐  ┌──────────────────┐  │
│  │    AI Model     │◄─►│  Sandboxed UI   │  │
│  └────────┬────────┘  └────────┬─────────┘  │
└───────────┼────────────────────┼────────────┘
            │   JSON-RPC over postMessage
            ▼                    ▼
      ┌──────────────────────────────┐
      │         MCP Server           │
      │  ┌────────┐  ┌────────────┐  │
      │  │ Tools  │  │ UI Templates│  │
      └──────────────────────────────┘
```

---

## **The Collaboration**

Built on proven implementations:

**MCP-UI** (open source):
- Demonstrated UI-as-MCP-resources pattern
- Adopted by Postman, Shopify, Hugging Face

**OpenAI Apps SDK**:
- Validated demand for rich UI in ChatGPT
- 800M+ users

**Result**: Anthropic, OpenAI, MCP-UI creators collaborated to standardize

---

## **OpenAI Apps SDK: Distribution Today**

| Aspect | Details |
|--------|---------|
| **What It Is** | MCP tools + Custom UI + ChatGPT integration |
| **Who Gets Access** | Business, Enterprise, Edu tiers |
| **What Platform Handles** | Billing, discovery, user acquisition |

---

## **Marketplace Monetization**

**Unlocks Marketplace revenue model**:
- 800M+ ChatGPT users
- Low customer acquisition cost
- Platform billing
- Volume play (many small customers vs few large contracts)

---

## **Build Now vs Build Later**

| Standard | Status | Recommendation |
|----------|--------|----------------|
| **Apps SDK** | Production-ready | **Use today** for ChatGPT distribution |
| **MCP Apps Extension** | Proposed (SEP-1865) | **Watch** for cross-platform future |

---

## **The Strategy**

1. **Build on Apps SDK** for distribution today
2. **Follow MCP Apps Extension** for portability tomorrow
3. Foundation (MCP) is **stable**
4. Interface layer is **standardizing**

---

**Bottom line**: MCP Apps Extension adds interactive UI to agents. Apps SDK gives immediate access to 800M users. Build on both for distribution now, portability later.


# Who's Behind AAIF

**Platinum Members (Major Tech Infrastructure Players):**
- AWS - Cloud infrastructure
- Anthropic - Claude AI, MCP
- Blockgoose, Square
- Bloomberg - Financial data
- Cloudflare - Edge computing
- Google - Gemini AI
- Microsoft - Azure, GitHub
- OpenAI - ChatGPT, AGENTS.md

**Gold Members:**
- 20+ companies including Salesforce, Shopify, Snowflake, IBM, Oracle, JetBrains, Docker

**Significance:**
- These are established infrastructure companies, not startups
- Their involvement signals genuine industry standardization
- These companies move deliberately on infrastructure decisions
- Their agreement on AAIF foundation indicates real commitment to standardization


# AAIF Impact on Agent Factory - Key Points

**CoCounsel Example:**
- $650M acquisition bought portable legal expertise, not platform-locked tech
- Scalability across entire operation was key

**AAIF Standards Enable Portability:**

| Your Asset | AAIF Standard | Monetization Impact |
|------------|---------------|---------------------|
| Tool integrations | MCP | Connect once, sell to any client |
| Domain expertise | Agent Skills | License on any platform |
| Client adaptability | AGENTS.md | Deploy without per-client customization |
| Architecture | goose | Production patterns from enterprise scale |
| Interface reach | MCP Apps + Apps SDK | 800M+ ChatGPT users, cross-platform |

**Digital SDR Example ($1,500/month):**
AAIF ensures it:
- Connects to ANY CRM via MCP (not just Salesforce)
- Works with ANY AI platform (portable standards)
- Adapts to ANY workflow via AGENTS.md
- Shows rich interfaces via MCP Apps
- Distributes to 800M+ users via Apps SDK

**WITHOUT AAIF:**
- Agents locked to one platform
- Each client = potential rebuild
- Expertise trapped, not portable
- Switching AI = starting over

**WITH AAIF:**
- Integrations work across all platforms
- Client diversity = strength
- Expertise compounds across all agents
- Provider switches = config changes, not rewrites

**Bottom Line:** AAIF transforms demos into sellable products with real portability and scale.