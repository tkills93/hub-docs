# Claude Code Cheat Sheet
## Check, Debug, Fix, and More

> New to Claude Code? Start with the
> [Getting Started guide](./claude-code-getting-started.md), then come back here
> as a reference.

---

## Checking & Reviewing Code

| What you want | What to say |
|---|---|
| Check a file for bugs | `"Check this file for bugs"` or paste the code |
| Review a whole PR | `/review` |
| Security audit of changes | `/security-review` |
| Find logic errors | `"Are there any logic errors in this function?"` |
| Verify a fix actually works | `/verify` |
| Spot code smells / simplify | `/simplify` |
| Lint-style review | `/code-review` or `/code-review --fix` to auto-apply |

---

## Debugging Errors

Paste the error message and say one of:

```
"Why is this failing?"
"What does this error mean?"
"Debug this traceback"
"What's causing this TypeError?"
```

**Provide context that helps:**
- The full error/stack trace
- The file and line number if known
- What you expected vs. what happened
- Any recent changes you made

**Example prompt:**
```
Getting this error in App.tsx:30 — TypeError: Cannot read properties
of undefined (reading 'map'). The data comes from an API call.
What's wrong?
```

---

## Fixing Errors

| Scenario | Prompt |
|---|---|
| Fix a specific bug | `"Fix this bug"` (paste error + code) |
| Fix all TypeScript errors | `"Fix all TS errors in this file"` |
| Fix a syntax error | Paste the code — Claude spots and fixes it |
| Fix and explain | `"Fix this and explain what was wrong"` |
| Auto-fix after review | `/code-review --fix` |

Claude edits files directly — no copy-paste needed.

---

## Getting Suggestions & Tips

```
"How should I approach X?"
"What's the best way to handle Y?"
"Suggest a cleaner way to write this"
"What are the trade-offs between A and B?"
"How would you improve this component?"
```

For architecture questions, Claude gives a recommendation + the main trade-off, then waits for your go-ahead before implementing.

---

## Slash Commands (Skills)

| Command | What it does |
|---|---|
| `/review` | Full PR review |
| `/code-review` | Code-level bug + cleanup review |
| `/code-review --fix` | Review and auto-apply fixes |
| `/code-review --comment` | Post findings as inline PR comments |
| `/simplify` | Refactor for clarity/efficiency |
| `/security-review` | Security audit of current branch changes |
| `/verify` | Run the app and confirm a change works |
| `/run` | Start the project and observe behavior |
| `/init` | Generate a CLAUDE.md for the repo |
| `/help` | General Claude Code help |
| `/config` | Change settings (theme, model, etc.) |
| `/fast` | Toggle Fast mode (Opus with faster output) |
| `/clear` | Clear conversation context |

---

## Useful Prompt Patterns

### "Explain, then fix"
```
Explain what this code does, then fix the bug on line 42.
```

### "Fix without changing behavior"
```
Fix the TypeError but don't change how the function works otherwise.
```

### "Show me the diff only"
```
What changes would you make? Don't edit the file yet — show me first.
```

### "Step-by-step debug"
```
Walk me through what this code does line by line and tell me
where it goes wrong.
```

### "Find all instances"
```
Find everywhere this pattern appears in the codebase and check
if any are broken.
```

### "Compare approaches"
```
Should I use useState or useReducer here? Give me a one-sentence
recommendation and the main trade-off.
```

---

## Workflow Tips

**Give Claude the error, not just the symptom**
- Bad: `"My app is broken"`
- Good: `"Getting 'Cannot read properties of undefined' on line 30 of App.tsx after the API call"`

**Paste relevant code, not the whole file**
For quick questions, paste just the function or block in question.

**Say what you've already tried**
```
"I tried checking for null but it still fails — what else could cause this?"
```

**Ask for one thing at a time**
Claude handles compound tasks well, but focused prompts get faster results.

**Let Claude read the file**
Instead of pasting, you can say: `"Look at src/components/Form.tsx and find the bug"` — Claude will read it directly.

---

## Git & PR Operations

| Task | What to say |
|---|---|
| Commit changes | `"Commit these changes"` |
| Create a PR | `"Create a pull request"` |
| Watch a PR for CI/review | `"Watch this PR and fix any failures"` |
| Check what changed | `"What's on this branch vs main?"` |
| Summarize recent commits | `"Summarize what's been done on this branch"` |

---

## What Claude Won't Do (Without Asking You First)

- Push to remote / force-push
- Delete files or branches
- Merge or close PRs
- Send messages or post comments publicly
- Run destructive commands (`rm -rf`, `reset --hard`, etc.)

Claude asks before any action that's hard to reverse or affects shared state.

---

## When Claude Gets Stuck

If Claude says it can't help or gives a wrong answer:

1. **Rephrase** — be more specific about the file, line, or behavior
2. **Add context** — paste the error, the relevant code, and what you expected
3. **Break it down** — ask one smaller question instead of a complex one
4. **Check `/help`** — for Claude Code CLI questions
5. **Report issues** — github.com/anthropics/claude-code/issues
