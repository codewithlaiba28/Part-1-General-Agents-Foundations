# EXAM KEY POINTS: Building Your Own Skills

## THE SKILL.MD FILE: TWO PARTS (CRITICAL STRUCTURE)

**Every skill = one folder with one required file: SKILL.md**

```
.claude/skills/meeting-notes/
└── SKILL.md    ← This is what you create
```

**Simplicity is intentional—anyone can create one.**

---

### PART 1: YAML FRONTMATTER (The ID Card)

```yaml
---
name: "meeting-notes"
description: "Transform meeting transcripts or raw notes into structured summaries with action items, decisions, and follow-ups. Use when user shares meeting content or asks for meeting notes."
---
```

**Required fields:**
- `name`: Skill identifier
- `description`: **MOST IMPORTANT** - determines when skill activates

---

### PART 2: MARKDOWN BODY (The Instructions)

```markdown
# Meeting Notes Skill

## When to Use
- User shares a meeting transcript
- User asks to summarize meeting notes

## Procedure
1. Extract action items with owners and deadlines
2. Highlight decisions made
3. Summarize discussion points
4. Flag open questions

## Output Format
**Action Items**
- [ ] Task — Owner — Deadline

**Decisions Made**
- Decision: [what] — Made by: [who]

## Quality Criteria
- Keep to one page maximum
- Don't transcribe verbatim
```

**That's a complete skill. No scripts required. No complex setup.**

---

## THE DESCRIPTION FIELD: ACTIVATION TRIGGER (MOST IMPORTANT)

**Critical concept:** The description determines when Claude activates your skill

**Why it matters:**
- Claude sees skill descriptions at startup (Level 1 architecture)
- Claude scans descriptions to decide which skills apply
- **Bad description = skill never activates**
- **Good description = skill activates at right times**

---

## GOOD VS BAD DESCRIPTIONS (TESTABLE)

### ❌ BAD: Too Vague
```yaml
description: "Helps with notes"
```
**Problem:** "notes" could mean anything. Claude won't know when to activate.

### ❌ BAD: Too Narrow
```yaml
description: "Summarizes Zoom meeting transcripts from the marketing team"
```
**Problem:** Won't activate for Teams calls, non-marketing meetings, or live notes.

### ✅ GOOD: Clear Context + Action
```yaml
description: "Transform meeting transcripts or raw notes into structured summaries with action items, decisions, and follow-ups. Use when user shares meeting content or asks for meeting notes."
```

**Why it works:**
1. States WHAT it does (transform → structured summaries)
2. Lists KEY OUTPUTS (action items, decisions, follow-ups)
3. Specifies WHEN to use (meeting content, meeting notes request)

---

## THE DESCRIPTION FORMULA (MEMORIZE)

```
[Action verb] + [input type] + [into/for] + [output type] + [key features].
Use when [trigger conditions].
```

### Examples:

**Blog Planning:**
```yaml
description: "Plan blog posts with topic research, outline creation, headline variations, and introduction drafts. Use when user asks to plan, outline, or write blog content."
```

**Code Review:**
```yaml
description: "Perform systematic code reviews checking security, performance, maintainability, and best practices. Use when user asks to review code or check for issues."
```

**Email Drafting:**
```yaml
description: "Draft professional emails matching specified tone and purpose. Use when user needs to write emails or requests communication help."
```

---

## THE FAST WAY: USE SKILL-CREATOR (RECOMMENDED)

**Power move:** Use Claude to create skills for you

### Workflow:

```bash
cd claude-code-skills-lab
claude
```

Then:
```
I want to create a skill for [your procedure]. Use the skill-creator to help me build it.
```

### Example:
```
I want to create a skill for writing technical documentation.
My procedure:
1. Start with a one-sentence summary
2. List prerequisites
3. Provide step-by-step instructions with code examples
4. End with troubleshooting section
5. Keep jargon minimal, explain terms on first use

Use the skill-creator to build this into a proper skill.
```

**The skill-creator guides you through:**
- Understanding your procedure
- Writing effective descriptions
- Generating complete SKILL.md file

**This is how most people should create skills.**

---

## CREATING YOUR FIRST SKILL: STEP-BY-STEP

### Step 1: Create the Folder
```bash
mkdir -p .claude/skills/blog-planner
```

### Step 2: Create SKILL.md

**File:** `.claude/skills/blog-planner/SKILL.md`

```yaml
---
name: "blog-planner"
description: "Plan engaging blog posts with topic research, structured outlines, headline variations, and compelling introductions. Use when user asks to plan, outline, or write blog content."
---

# Blog Planning Skill

## When to Use This Skill
- User asks to "plan a blog post" or "write an article"
- User mentions blog topics, headlines, or content strategy
- User needs help structuring written content

## Procedure
1. **Understand the topic**: Clarify subject and target audience
2. **Create outline**: Structure into 3-5 main sections
3. **Generate headlines**: Provide 5 variations (curiosity-driven, benefit-focused, direct)
4. **Draft introduction**: Write a hook that challenges assumptions or poses a question

## Output Format
**Topic Summary**: 2-3 sentence overview
**Target Audience**: Who should read this?
**Outline**: Numbered list of main sections with brief descriptions
**Headline Options**: 5 variations
**Introduction Draft**: 1-2 paragraph hook

## Quality Criteria
- Headlines: Curiosity-driven, never clickbait
- Introductions: Challenge assumptions or pose unexpected questions
- Outlines: Problem → failed solutions → insight → application structure
- Specificity: Use numbers over vague claims ("30% improvement" not "significant gains")
```

### Step 3: Test Your Skill

```bash
claude
```

```
Help me plan a blog post about learning AI tools as a beginner
```

**Watch for:**
- Does Claude follow the procedure?
- Does output match the format?
- Does quality match your criteria?

### Step 4: Verify Activation

```
What skills are you using in our conversation? Did you activate the blog-planner skill?
```

**This confirms skill loaded and helps understand activation mechanism.**

---

## SKILL SECTIONS EXPLAINED (TESTABLE)

| Section | Purpose | Required? |
|---------|---------|-----------|
| **YAML Frontmatter** | Name and activation trigger | ✅ Required |
| **When to Use** | Explicit activation conditions | ⚠️ Recommended |
| **Procedure** | Step-by-step instructions | ✅ Required |
| **Output Format** | Exact structure of deliverable | ✅ Required |
| **Quality Criteria** | Standards for good output | ⚠️ Recommended |
| **Example** | Sample input/output | ⚠️ Recommended |

---

## REFINING SKILLS: THE CO-LEARNING CYCLE

**Your first version won't be perfect. That's expected.**

### Phase 1: AI as Teacher

```
Review my blog-planner skill. What could be improved?
Suggest 2-3 specific enhancements.
```

**Claude might suggest:**
- Add SEO considerations to outline section
- Include word count targets for each section
- Add "common mistakes to avoid" section

### Phase 2: You as Teacher

```
Good suggestions, but I have constraints:
- Headlines must be curiosity-driven, NEVER clickbait
- I prefer problem → insight → application structure
- Keep introductions under 100 words

Update the skill with these constraints.
```

### Phase 3: Convergence

Together you refine until skill matches your actual workflow.

---

## ITERATION PROMPTS (PRACTICAL EXAMPLES)

### After Using Skill Multiple Times:

```
I've used the blog-planner skill 3 times now. Here's what worked and what didn't:
- Worked: Headline variations are great
- Didn't work: Outlines are too generic, need more specific section descriptions

Help me update the skill to fix the outline issue.
```

### Compare to Real Usage:

```
Compare the blog-planner output to how I actually wrote my last blog post.
What's different? Should we update the skill to match my real style?
```

---

## COMPLETE SKILL EXAMPLE (REFERENCE)

**Meeting Notes Skill:**

```yaml
---
name: "meeting-notes"
description: "Transform meeting transcripts or raw notes into structured summaries with action items, decisions, and follow-ups. Use when user shares meeting content or asks for meeting notes."
---

# Meeting Notes Skill

## When to Use
- User shares a meeting transcript
- User asks to summarize meeting notes
- User mentions "action items" or "meeting summary"

## Procedure
1. Extract action items with owners and deadlines
2. Highlight decisions made (with who made them)
3. Summarize discussion points (don't transcribe verbatim)
4. Flag open questions for follow-up
5. Keep to one page maximum

## Output Format

**Action Items** (top of document)
- [ ] Task — Owner — Deadline

**Decisions Made**
- Decision: [what] — Made by: [who]

**Discussion Summary**
Brief bullets, not transcription.

**Open Questions**
- Question needing follow-up

## Quality Criteria
- One page maximum
- No verbatim transcription
- Clear ownership for all action items
- Date format: YYYY-MM-DD

## Example

**Input**: "Meeting about Q2 launch. Sarah proposed moving deadline to May 15. Team agreed. John will design mockups by April 30. Discussion on budget constraints - need to decide between feature A or B."

**Output**:

**Action Items**
- [ ] Design mockups — John — 2025-04-30

**Decisions Made**
- Decision: Move Q2 launch deadline to May 15 — Made by: Team consensus (Sarah's proposal)

**Discussion Summary**
- Budget constraints require choosing between feature A or B (decision pending)

**Open Questions**
- Which feature to prioritize: A or B?
```

---

## QUALITY CRITERIA BEST PRACTICES

**Always include quality criteria:**

### Examples:

**For Writing:**
- Headlines: Curiosity-driven, never clickbait
- Tone: Professional but conversational
- Length: 800-1200 words

**For Code:**
- Follow PEP 8 style guide
- Include docstrings for all functions
- No hardcoded credentials

**For Data:**
- Date format: YYYY-MM-DD
- Currency: USD with 2 decimal places
- Missing values: "N/A" not blank

**Why:** Quality criteria constrain non-determinism within YOUR standards

---

## MARKDOWN REFRESHER (PREREQUISITE)

**Before creating skills, you should know:**

- Headers (`#`, `##`, `###`)
- Bullet points (`-`, `*`)
- Code blocks (` ``` `)
- YAML syntax (`---` frontmatter)

**If not comfortable:** Review Chapter 2: Markdown for AI-Native Development

---

## TESTING WORKFLOW (STEP-BY-STEP)

### 1. Create Skill
```bash
mkdir -p .claude/skills/[skill-name]
# Create SKILL.md file
```

### 2. Start Claude
```bash
claude
```

### 3. Test Activation
```
[Ask for something the skill should handle]
```

### 4. Verify
```
What skills are you using? Did [skill-name] activate?
```

### 5. Refine
```
The output was good, but [specific improvement needed].
Update the skill to fix this.
```

### 6. Test Again
```
[Try the same request with updated skill]
```

---

## WHERE SKILLS LIVE (FILE STRUCTURE)

```
your-project/
├── .claude/
│   └── skills/
│       ├── blog-planner/
│       │   └── SKILL.md
│       ├── meeting-notes/
│       │   └── SKILL.md
│       └── code-review/
│           ├── SKILL.md
│           └── checklist.md    ← Optional supporting file
├── CLAUDE.md
└── src/
```

**Key points:**
- Skills in `.claude/skills/` directory
- Each skill = one folder
- Required: `SKILL.md`
- Optional: Supporting files (templates, scripts, checklists)

---

## SKILL SUITES (THINKING IN ECOSYSTEMS)

**Don't create isolated skills—create skill ecosystems**

### Example: Content Creation Suite

```
.claude/skills/
├── blog-planner/          # Plans blog posts
├── headline-writer/       # Generates headlines
├── intro-writer/          # Writes compelling intros
├── seo-optimizer/         # Checks SEO
└── social-media-promo/    # Creates promotional posts
```

**Skills that complement each other create more value than skills that work alone.**

---

## COMMON MISTAKES TO AVOID

❌ **Vague descriptions** ("Helps with writing")  
❌ **Too narrow descriptions** (won't activate when needed)  
❌ **Missing quality criteria** (output varies too much)  
❌ **No examples** (Claude doesn't understand format)  
❌ **Overly complex procedures** (hard to follow)  
❌ **Not testing activation** (skill exists but never runs)  
❌ **Creating skills in isolation** (not thinking in suites)  

---

## CONNECTIONS TO OTHER LESSONS

**Builds on:**
- Lesson 5: CLAUDE.md (project context)
- Lesson 7: Why encode procedures (personal benefit)
- Lesson 8: Skills architecture (conceptual foundation)

**This lesson (9):**
- HOW to build skills (hands-on creation)

**Leads to:**
- Lesson 10: Agent Skills Exercises (27 hands-on practices)
- Lesson 11-13: Subagents and MCP (complementary tools)
- Part 6/Chapter 16: Custom Agents using skills

---

## THE BIGGER PICTURE

**Skills you create now = building blocks for larger systems**

In Part 6:
- Build Custom Agents using SDKs
- Skills integrate directly into those agents
- Skills are reusable intellectual property
- Value compounds over time

**Create once, use everywhere.**

---

## QUICK REFERENCE CARD

| Component | What It Is | Example |
|-----------|------------|---------|
| **Folder** | `.claude/skills/[name]/` | `.claude/skills/blog-planner/` |
| **Required File** | `SKILL.md` | Contains YAML + Markdown |
| **YAML** | Frontmatter with metadata | `name:`, `description:` |
| **Description** | Activation trigger | Use description formula |
| **Markdown** | Instructions | When to Use, Procedure, Format, Criteria |

---

## EXAM SCENARIO QUESTIONS

### Q: "What's the most important part of a skill?"
**A:** The description field in YAML frontmatter—it determines when the skill activates.

### Q: "How do I know if my skill activated?"
**A:** Ask Claude: "What skills are you using in our conversation?"

### Q: "My skill never activates. What's wrong?"
**A:** Check the description—likely too vague or too narrow. Use the description formula.

### Q: "What's the minimum required for a skill?"
**A:** One folder with one `SKILL.md` file containing YAML frontmatter (name, description) and markdown instructions.

### Q: "Should I create skills from scratch or use skill-creator?"
**A:** Use skill-creator (faster, better results). Understanding the structure helps refine later.

### Q: "How do I improve a skill?"
**A:** Use the co-learning cycle: (1) AI suggests improvements, (2) You add constraints, (3) Converge on optimal version.

---

## BOTTOM LINE FOR EXAM

**Skill creation workflow:**
1. **Create folder:** `.claude/skills/[skill-name]/`
2. **Write SKILL.md** with two parts: YAML frontmatter + Markdown body
3. **Description is critical:** Use the formula (action + input + output + trigger)
4. **Test activation:** Ask Claude what skills are active
5. **Refine through co-learning:** AI teaches, you teach, converge

**Fast way:** Use skill-creator (recommended)

**Key sections:** When to Use, Procedure, Output Format, Quality Criteria, Example

**Testing:** Create → Test → Verify → Refine → Test Again

**Think in ecosystems:** Skills that work together > isolated skills

**Your first version won't be perfect—iteration is expected**