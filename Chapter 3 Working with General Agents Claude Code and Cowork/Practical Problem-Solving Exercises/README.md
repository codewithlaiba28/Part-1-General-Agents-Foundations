# Practical Problem-Solving Exercises

## THREE CORE SKILLS (MEMORIZE)

These run through EVERY exercise:

1. **Problem Decomposition** - Breaking vague problems into clear steps
2. **Specification Writing** - Describing outcomes precisely enough for an agent to execute
3. **Quality Verification** - Checking whether output actually solves your problem

---

## 7-STEP PROBLEM-SOLVING FRAMEWORK (CRITICAL)

Use for EVERY exercise:

1. **Define the Problem** - What exactly am I trying to accomplish? What does "done" look like?
2. **Gather Context** - What files, data, or information does Claude need?
3. **Write the Spec** - Describe desired outcome, constraints, and format
4. **Execute** - Run it with Claude Code or Cowork
5. **Verify** - Does output match what I asked for? Is it correct?
6. **Iterate** - What would I change? Run again with improvements
7. **Reflect** - What did I learn about specifying problems clearly?

**This framework isn't just for exercises—it's how professionals work with AI agents every day.**

---

## 5-CRITERIA ASSESSMENT RUBRIC

| Criteria | What It Measures |
|----------|------------------|
| **Problem Clarity** | Can you define clear success criteria and anticipate edge cases? |
| **Specification Quality** | Are your specs structured, unambiguous, and reusable? |
| **Output Verification** | Do you test against requirements and edge cases? |
| **Iteration** | Do you have a systematic approach to refinement? |
| **Reflection** | Can you derive principles for next time? |

**Progression:** Beginner (1) → Developing (2) → Proficient (3) → Advanced (4)

---

## 8 MODULES: WHAT EACH TEACHES

### Module 1: File Organization & Digital Housekeeping
**Core Skill:** Turning chaos into structure by describing organizational rules clearly

**Key Exercises:**
- Messy Downloads Folder
- Photo Album Builder
- Inbox Zero Challenge

**Key Lesson:** Vague instructions produce unpredictable results. The more specific your outcome description, the better the result.

---

### Module 2: Research & Information Synthesis
**Core Skill:** Turning a broad question into a structured research task with clear deliverables

**Key Exercises:**
- Comparison Matrix
- Literature Review
- Decision Document

**Key Lesson:** Research quality depends on how well you define what you're looking for. The same question with different criteria produces completely different recommendations.

---

### Module 3: Data Wrangling & Analysis (No Coding Required)
**Core Skill:** Describing data transformations in plain English and verifying results

**Key Exercises:**
- Messy Spreadsheet
- Survey Analyzer
- Budget Tracker

**Key Lesson:** "Show me the plan first" is crucial for data tasks. Always require preview before execution.

---

### Module 4: Document Creation & Transformation
**Core Skill:** Turning raw information into polished, professional deliverables

**Key Exercises:**
- Meeting Notes Transformer
- Report Generator
- Presentation Builder

**Key Lesson:** Different audiences need the same information in different forms. Specify format AND audience.

---

### Module 5: Process Automation & Workflows
**Core Skill:** Identifying repetitive patterns and describing them as repeatable processes

**Key Exercises:**
- Batch Renamer
- Template System
- Weekly Report Automator

**Key Lesson:** Separate "data that changes" from "process that stays the same." Write specifications that are reusable, not one-shot.

---

### Module 6: Problem Solving & Creative Thinking
**Core Skill:** Using Claude as a thinking partner for open-ended problems

**Key Exercises:**
- Business Plan Skeleton
- Troubleshooter
- Event Planner

**Key Lesson:** Problem-solving is iterative, not one-shot. Have conversations, don't just request documents.

---

### Module 7: Quality Control & Critical Thinking
**Core Skill:** Not blindly trusting AI output—learning to verify, critique, and improve

**Key Exercises:**
- Fact Checker
- Specification Stress Test
- Prompt Tournament

**Key Lesson:** AI outputs can sound confident but be wrong. Fact-checking is a skill humans MUST provide.

---

### Module 8: Capstone Projects
**Core Skill:** Combining all skills on self-directed projects

**Options:**
- Personal Knowledge Base
- Small Business Operations Kit
- Course Material Generator

**Key Lesson:** No starter prompts—design the entire approach yourself.

---

## CRITICAL PATTERNS TO MEMORIZE

### Vague vs Better Prompts

**Pattern 1: File Organization**
- ❌ Vague: "Organize these files"
- ✅ Better: Define categories, naming convention, duplicate handling, preservation of originals

**Pattern 2: Research**
- ❌ Vague: "Compare React, Vue, and Angular"
- ✅ Better: Define context, specific comparison criteria (5-7 factors), target audience

**Pattern 3: Data Cleaning**
- ❌ Vague: "Clean up this spreadsheet"
- ✅ Better: "Before making changes, show me what you plan to do. Specify date format, name capitalization, duplicate definition"

---

## TWO APPROACHES TO TASKS (TESTABLE)

### Outcome-Focused vs Step-by-Step

**Outcome-Focused:**
```
"I want a photo gallery organized by orientation with duplicates flagged"
```

**Step-by-Step:**
```
1. Sort images by orientation
2. Create portrait folder
3. Create landscape folder
4. Check for duplicates
5. Flag duplicates in a log
6. Generate HTML gallery
```

**Compare results:** Which approach produced better outcome? Which was faster?

---

## KEY DISTINCTIONS (EXAM QUESTIONS)

### "Find Information" vs "Synthesize Knowledge"
- **Find:** Collect sources
- **Synthesize:** Organize by theme, identify consensus/debate, fill knowledge gaps

### "Combine Files" vs "Synthesize into Narrative"
- **Combine:** Copy-paste from multiple sources
- **Synthesize:** Create coherent story across sources

### "Distill" vs "Copy-Paste into Slides"
- **Distill:** Extract essence, maintain narrative
- **Copy-Paste:** Transfer text verbatim

---

## IMPORTANT META-LESSONS

### 1. Idempotency
**Definition:** Safe to run repeatedly without causing problems

**Example:** Rename script that:
- ✅ Has logic to skip already-renamed files
- ✅ Logs all changes
- ❌ Would corrupt files if run twice

### 2. Template + Data = Output
**Pattern:** Separation of content from presentation

**Example:**
- Template: `certificate_template.md` with `{{NAME}}`, `{{DATE}}`
- Data: `student_data.csv`
- Output: 10 personalized certificates

### 3. Preview Before Execution
**Critical for:**
- Batch operations
- Data transformations
- Irreversible changes

**Always include:** "Show me the plan first and get my approval"

### 4. Consistency Constraints
**When creating multiple outputs:**

"All three outputs must be consistent—the same decisions and action items should appear across all formats"

**Example:** Meeting notes → Minutes, Action Items, Executive Summary

---

## REFLECTION QUESTIONS (APPEAR ON EVERY EXERCISE)

Common question types:
1. **Expectation vs Reality:** Did output match expectations? If not, what was different?
2. **Missed Specifications:** What did you forget to specify?
3. **Reusability:** Could you run this again next week/month?
4. **Edge Cases:** What scenarios didn't you anticipate?
5. **Iteration:** What would you change the second time?

---

## TOOLS (TESTABLE)

**Two Options:**
- 🖥️ **Claude Code** - Terminal-based, for CLI-comfortable students
- 🗂️ **Cowork** - Desktop app, point at folder

**Most exercises work with either tool.**

---

## SPECIFICATION QUALITY PROGRESSION

### Beginner (Level 1):
- Vague, one-sentence instructions
- Copies starter prompts as-is
- Accepts first output

### Proficient (Level 3):
- Structured, unambiguous specs
- Defined clear success criteria
- Verified against requirements

### Advanced (Level 4):
- Reusable, parameterized specs
- Anticipated edge cases
- Tested edge cases and refined systematically

---

## CRITICAL "ALWAYS INCLUDE" INSTRUCTIONS

### For Data Tasks:
"Before making changes, show me what you plan to do and get my approval"

### For Multi-Output Tasks:
"All outputs must be consistent across formats"

### For Batch Operations:
"Create a log of all changes made" + "Make this idempotent (safe to run repeatedly)"

### For Research Tasks:
Define: context, criteria (5-7 specific), audience, depth

---

## COMMON MISTAKES TO AVOID

❌ Accepting first output without verification  
❌ Forgetting to specify output format  
❌ Not defining edge case handling  
❌ Assuming Claude knows your priorities  
❌ Skipping the "preview before execution" step  
❌ Writing one-shot specs instead of reusable ones  
❌ Not testing if spec works with different data  

---

## WORKFLOW FOR EVERY EXERCISE

1. **Open exercise folder** from `claude-code-basic-exercises/`
2. **Read INSTRUCTIONS.md** in the folder
3. **Read walkthrough** for context
4. **Start Claude Code/Cowork** in exercise folder
5. **Write your own prompts** (don't just copy starter)
6. **Reflect** using provided questions

---

## CONNECTIONS TO OTHER LESSONS

**Builds on:**
- Lessons 1-5: Understanding AI agents, CLAUDE.md, basic conversations

**Prepares for:**
- Lesson 7: Teach Claude Your Way (custom instructions)
- Lessons 8-9: Agent Skills (reusable expertise files)

**Key Insight:** These exercises practice manually what Skills will automate later.

---

## BOTTOM LINE FOR EXAM

**Three skills run through every exercise:**
1. Problem Decomposition
2. Specification Writing
3. Quality Verification

**Use the 7-step framework every time.**

**Know the difference between:**
- Vague vs Better prompts
- Outcome-focused vs Step-by-step
- Find vs Synthesize
- Combine vs Synthesize into narrative

**Always include:**
- Preview before execution (data tasks)
- Consistency constraints (multi-output)
- Idempotency (batch operations)
- Clear success criteria

**Skills compound:** Every exercise makes the next easier by building intuition for communicating with AI agents.