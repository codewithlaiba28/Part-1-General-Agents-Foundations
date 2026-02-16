**Headings - Creating Document Hierarchy**

**Hash Symbols for Headings:**
```
# Level 1 (Largest - Title)
## Level 2 (Main sections)
### Level 3 (Subsections)
#### Level 4 (Deep details)
##### Level 5 (Avoid in specs)
###### Level 6 (Avoid in specs)
```

**Heading Purposes:**
- **Level 1 (#)**: Document title (use ONCE)
- **Level 2 (##)**: Main sections (Problem, Features, Installation)
- **Level 3 (###)**: Subsections within main sections
- **Level 4 (####)**: Deep technical details
- **Level 5-6**: Avoid (too complex)

**Proper Hierarchy Rule:**
- NEVER skip levels
- Think: Folders → Subfolders → Files
- Must go: # → ## → ### (sequential)

**Example Structure:**
```
# Task Tracker App
## Problem
## Features
### Add Tasks
### View Tasks
## Expected Output
## Installation
```

**Common Mistakes:**
1. ❌ `#NoSpace` → ✅ `# Space Required`
2. ❌ Multiple # (Level 1) → ✅ One # only
3. ❌ Skip levels (# to ###) → ✅ # → ## → ###

**Why It Matters:**
- AI parses structure faster
- AI validates completeness
- AI generates better code
- 30-50% faster implementation

**Accessibility:**
- Screen readers need proper hierarchy
- AI agents need logical structure
- Professional documentation standard