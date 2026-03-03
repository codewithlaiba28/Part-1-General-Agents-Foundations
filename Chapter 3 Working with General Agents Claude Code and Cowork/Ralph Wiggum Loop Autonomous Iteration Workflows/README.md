# Ralph Wiggum Loop: Key Points

## The Core Problem
**Manual iteration fatigue:** You ask Claude to fix 47 linting errors → copy output → paste back → repeat 10+ times over 30 minutes. You become a manual feedback loop operator instead of doing productive work.

## What Ralph Loop Solves
**Autonomous iteration** - Claude runs task → checks result → identifies problems → fixes → repeats until completion criteria met, all without your intervention.

```
Normal flow:
You ask → Claude fixes → Session ends → You check → Copy errors → Paste back → Repeat...

Ralph Loop flow:
You ask → Claude fixes → Stop hook intercepts → Reinjects "continue" → Claude fixes more → Repeats until done
```

## How It Works (Stop Hook)
```
Claude: "Fixed 5 files. 32 problems remaining. I'm done."
  ↓
Stop Hook: "Did you see '0 problems'? No? Continue fixing."
  ↓
Claude: "Fixed 4 more. 18 problems remaining. I'm done."
  ↓
Stop Hook: "Did you see '0 problems'? No? Continue."
  ↓
Claude: "All fixed. 0 problems. I'm done."
  ↓
Stop Hook: "You're actually done now." [STOPS]
```

## Installation
```bash
# Add marketplace
/plugin marketplace add anthropics/claude-plugins-official

# Install plugin
/plugin install ralph-loop@claude-plugins-official

# Verify
/ralph-loop --help
```

## Decision Framework: When to Use

**✅ Good fit:**
- 10+ expected iterations
- Clear success signal (tests pass, build succeeds, "0 errors")
- Single well-defined goal
- Errors provide clear feedback
- Can check back in 30-60 min

**❌ Poor fit:**
- Subjective quality assessment
- Human judgment required (strategy, aesthetics, priorities)
- Exploratory research
- Multi-goal tasks ("fix bugs AND add features")
- Waiting for external input (API keys, approvals)

**Golden rule:** Use when success is objective, verifiable, deterministic—measurable by tools, NOT human judgment.

## Usage Pattern (Recommended: Embedded Promise)

```bash
/ralph-loop "Task description:
- Specific requirement 1
- Specific requirement 2
- Verification step
Output <promise>COMPLETION_MARKER</promise> when done." \
--max-iterations LIMIT \
--completion-promise "COMPLETION_MARKER"
```

**Real example:**
```bash
/ralph-loop "Fix all ESLint errors:
- Run ESLint on all files
- Fix each error
- Re-run ESLint to verify
Output <promise>LINTING_COMPLETE</promise> when done." \
--max-iterations 20 \
--completion-promise "LINTING_COMPLETE"
```

## Why Embedded Promise Pattern?
- **You control the exact completion signal** (not dependent on tool output)
- **Claude knows what to output when complete** (explicit contract)
- **More reliable** across different tools/environments
- **Works with static completion promises** (set once at loop start)

**Alternative (natural tool output):**
```bash
/ralph-loop "Fix all TypeScript errors" --max-iterations 20 --completion-promise "Found 0 errors"
```

## Critical Safety Rule
**ALWAYS set `--max-iterations`** - Never run without a limit.

**Cost reality:**
| Task | Iterations | Cost |
|------|------------|------|
| Simple fix | 15-20 | $10-20 |
| Medium task | 30-40 | $30-60 |
| Complex refactor | 50-80 | $80-150 |
| 14hr upgrade | Unlimited | $50-100+ |

## Completion Promise: STATIC
**Critical limitation:** `--completion-promise` is set ONCE at loop start and CANNOT be changed during runtime.

❌ You cannot:
- Add promise after starting
- Modify mid-loop
- Use multiple conditions

✅ You must:
- Get it right at initial `/ralph-loop` command
- Use exact string matching
- Rely on `--max-iterations` as primary safety net

## Good Use Cases

| Task | Completion Promise | Why It Works |
|------|-------------------|--------------|
| Framework upgrade | "build completed successfully" | Build errors give clear feedback |
| Test-driven refactor | "All 47 tests passing" | Tests provide immediate verification |
| Linting/type errors | "tsc reports 0 errors" | Compiler output is deterministic |
| Deployment debug | "Health check: 200 OK" | HTTP status is objective |

## When to Cancel (`/cancel-ralph`)
- Same error repeats 3+ times (Claude is stuck)
- Iteration count grows faster than progress
- Claude makes unrelated changes
- External dependency issue (API key, network)

## Best Practices
1. **Before starting:**
   ```bash
   git checkout -b my-task
   git commit -am "Checkpoint before Ralph Loop"
   ```

2. **Use embedded promise pattern** for reliability
3. **Start conservative** (20 iterations), increase if needed
4. **Provide context in CLAUDE.md** (project structure, test commands)
5. **Monitor every 15-30 minutes** (not constant attention)
6. **Review results** - Don't blindly accept

## Max Iterations Guide

| Complexity | Max Iterations | Expected Cost |
|------------|----------------|---------------|
| Simple (5-10 errors) | 15-20 | $10-20 |
| Medium (10-30 errors) | 30-40 | $30-60 |
| Complex (50+ errors) | 50-80 | $80-150 |

**Conservative approach:** Start with 20. If hits limit without completing, restart with higher limit or break task into smaller chunks.

## Bottom Line
**Eliminate iteration fatigue.** When you have 10+ iterations with objective completion criteria, Ralph Loop runs the feedback loop autonomously while you do productive work. Always use safety guardrails (`--max-iterations`, version control, cost monitoring).