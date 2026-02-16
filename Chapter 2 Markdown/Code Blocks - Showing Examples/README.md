**Code Blocks - Showing Examples - Notes:**

**Problem Without Code Blocks:**
- AI guesses output format
- Multiple possible interpretations
- Ambiguous specifications

**Solution: Show Exact Format**

**1. Fenced Code Blocks (Multiple Lines)**
```
Line 1
Line 2
Line 3
```

**Syntax:**
- Triple backticks (```)
- Code/output goes between
- Shows exact expected output

**2. Language Tags (For Clarity)**
```python
print("Hello")
```

**Common Tags:**
- `python` - Python code
- `bash` - Terminal commands
- `text` - Plain output
- `typescript` - TypeScript
- `json` - Data formats
- `yaml` - Config files

**Why Tags Matter:**
- AI knows which language to generate
- Correct syntax highlighting
- Prevents syntax mixing
- Applies language rules (e.g., PEP 8 for Python)

**3. Inline Code (Single Backticks)**
```
Use `python app.py` to run
Edit `config.py` file
Set `DEBUG` variable
```

**When to Use Inline:**
- Command names: `python`, `git`
- Variable names: `user_name`
- File names: `README.md`
- Function names: `calculate_total()`
- Short code in sentences

**Fenced vs Inline:**
- **Fenced (```)**: Multi-line code, output, examples
- **Inline (`code`)**: Commands, variables, files in text

**Pro-Tip: Show Edge Cases**
```text
No tasks yet. Use option 1 to add a task.
```
- Shows AI how to handle empty states
- Improves error handling

**Common Mistakes:**
1. ❌ Forgetting closing ``` 
2. ❌ Inline for multiple lines
3. ❌ No language tag when needed

**Why It Matters:**
- Exact output format → No guessing
- Semantic anchoring → Literal strings
- Specification by example → 60-80% fewer questions
- Code block = acceptance test

**Key:** Stop describing. Start demonstrating.