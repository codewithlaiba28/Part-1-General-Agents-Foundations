**Lists - Organizing Ideas**

**Two Types of Lists:**

**1. Unordered Lists (Bullet Points)**
```
- First item
- Second item
  - Nested item (2 spaces indent)
```

**When to Use:**
- No specific sequence needed
- Order doesn't matter
- Features, requirements, options
- Items are independent

**Example:**
```
## Features
- Add tasks
- View tasks
- Delete tasks
```

**2. Ordered Lists (Numbered Steps)**
```
1. First step
2. Second step
3. Third step
```

**When to Use:**
- Steps must be in sequence
- Order matters for correctness
- Installation, workflows, procedures
- Each step depends on previous

**Example:**
```
## Installation
1. Install Python 3.9+
2. Download project files
3. Navigate to folder
4. Run program
```

**Decision Guide:**
Ask: "Does order matter?"
- NO → Unordered (-)
- YES → Ordered (1.)

**Common Mistakes:**
1. ❌ `-NoSpace` → ✅ `- Space required`
2. ❌ Ordered for features → ✅ Unordered for features
3. ❌ Unordered for steps → ✅ Ordered for steps

**Pro-Tip: Nested Lists vs Headings**
- Use headings for major sections
- Use nested lists for details within section
- 10+ headings? → Consider nested lists instead

**Why It Matters:**
- AI identifies distinct items
- AI understands dependencies
- AI generates sequential code
- Semantic clarity = better code

**Key:** List type = semantic information for AI