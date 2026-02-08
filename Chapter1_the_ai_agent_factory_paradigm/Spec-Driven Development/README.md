# Spec-Driven Development (SDD) 

## **Core Concept**
**SDD Definition**: Write complete specifications BEFORE writing code. AI agents implement against specs while you focus on design, architecture, and validation.

### **The Core Equation** ⭐
```
Vague Idea + AI = 5+ iterations of misalignment
Clear Specification + AI = 1-2 iterations of refinement
```

---

## **Six Phases of SDD Workflow** (Most Important!)

| **Phase** | **Question** | **Output** | **Key Elements** |
|-----------|--------------|-----------|------------------|
| **1. Specify** | What are we building and why? | Specification document | • Intent (why it exists)<br>• Success Criteria (measurable)<br>• Constraints (limits)<br>• Non-Goals (what NOT to build) |
| **2. Clarify** | What's underspecified or ambiguous? | Clarification Q&A | • Edge cases<br>• Integration points<br>• Error handling<br>• Business logic |
| **3. Plan** | How will we build this? | Implementation plan | • Architecture<br>• Dependency sequence<br>• Testing strategy<br>• Tradeoffs |
| **4. Tasks** | What are concrete work items? | Task list with dependencies | • Each task with acceptance criteria<br>• Dependencies clear<br>• No task > 2 hours<br>• Correct order |
| **5. Implement** | How do we execute? | Working code | • AI executes plan<br>• Human reviews code<br>• Run tests<br>• Iterate if needed |
| **6. Validate** | Did we build what we specified? | Validation report | • All success criteria met<br>• Constraints satisfied<br>• Edge cases tested<br>• Documentation updated |

---

## **Four Characteristics of Good Specifications** ⭐

| **Characteristic** | **Bad Example** | **Good Example** |
|-------------------|-----------------|------------------|
| **1. Clarity** | "Make it fast" | "Response time < 200ms for 95th percentile" |
| **2. Completeness** | Missing edge cases | Covers: inputs, outputs, edge cases, states, performance, security |
| **3. Constraints** | No boundaries defined | Technical, business, and design constraints explicit |
| **4. Testability** | "User-friendly" | "New users complete registration in < 60 seconds" |

---

## **SDD vs Vibe Coding** (Important Comparison!)

| **Aspect** | **Vibe Coding** | **Spec-Driven Development** |
|------------|-----------------|----------------------------|
| **Starting Point** | Open IDE, start coding | Write specification first |
| **Decision Making** | Figure it out while coding | Make decisions upfront |
| **Iteration** | 5-10 cycles of "fix what I forgot" | 1-2 cycles of refinement |
| **Edge Cases** | Discovered in production | Planned in advance |
| **AI Collaboration** | "Build me a thing" (AI guesses) | "Implement this spec" (precision) |
| **Time Distribution** | 80% coding, 20% fixing | 20% specifying, 80% building |
| **Scalability** | Falls apart beyond 1,000 lines | Scales to complex systems |

---

## **When to Use SDD** (Decision Framework)

### ✅ **Use Full SDD When:**
- Production features (user-facing, business impact)
- Complex systems (multiple components)
- Security-critical (auth, payments, data)
- Team projects (shared understanding needed)
- AI-assisted development

### ⚡ **Use Lightweight SDD When:**
- Simple utilities (internal tools, scripts)
- Prototype code (exploratory work)
- Well-understood patterns (CRUD APIs)

### ❌ **Skip SDD When:**
- Learning experiments (exploring new tech)
- Throwaway prototypes (won't reach production)
- Trivial changes (fixing typo, updating color)

---

## **Common SDD Mistakes** (Remember These!)

| **Mistake** | **Why It Fails** | **Fix** |
|-------------|------------------|---------|
| **Writing spec after code** | Documenting decisions, not making them | Write spec FIRST |
| **Vague success criteria** | Not testable, can't verify success | Make every criterion measurable |
| **Skipping non-goals** | Scope creeps constantly | Explicitly list what NOT building |
| **Treating specs as static** | Spec becomes outdated | Update specs when requirements change |

---

## **Quality Gates Per Phase** ⭐

| **Phase** | **Must Pass Before Next Phase** |
|-----------|----------------------------------|
| **Specify** | Intent clear, criteria measurable, constraints explicit, non-goals defined |
| **Clarify** | All ambiguous terms defined, edge cases identified |
| **Plan** | Architecture exists, dependencies identified, testing strategy defined |
| **Tasks** | Each task has acceptance criteria, dependencies explicit, tasks < 2 hours |
| **Implement** | Code follows spec, tests pass, code review approved |
| **Validate** | All success criteria met, constraints satisfied, documentation updated |

---

## **Key Benefits** (Why SDD Matters)
1. **Eliminates guesswork** - AI knows exactly what to build
2. **Reduces iterations** - From 5+ to 1-2 cycles
3. **Scales to complexity** - Works for large systems
4. **Team coordination** - Everyone reads the spec
5. **Quality built-in** - Validation at every phase

---

## **Remember for Exam:**
- SDD = **Specification FIRST, then code**
- **Six phases** are sequential (each builds on previous)
- **Four characteristics** of good specs: Clarity, Completeness, Constraints, Testability
- Core equation: **Clear spec = fewer iterations**
- Quality gates **must pass** before moving to next phase