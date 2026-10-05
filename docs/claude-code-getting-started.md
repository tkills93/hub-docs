# Getting Started with Claude Code

New here? Read this first. It takes five minutes and covers everything you need
to start fixing real code. For the full command reference, see the
[Cheat Sheet](./claude-code-cheatsheet.md).

---

## What this actually is

Claude Code is **not** a chat window you paste code into.

It's an assistant working *inside your repository*. It can open your files, read
them, change them, run commands, and commit the results. You describe what you
want in plain English — it does the rest.

```
You:  There's a bug in the analyzer component, fix it
Me:   [opens the file] [finds the bug] [edits the file]
      Fixed — there was a stray space in a variable name on line 268.
```

You did not paste any code. That's the whole idea.

---

## Your first five minutes

Here's a real bug that's sitting in this repo right now. Follow along.

**Step 1 — Ask for a check.** Type:

```
check the analyzer component for errors
```

I'll open the file and report back. In this case:

> Found a syntax error on line 268: `value={charges.county Cost}` has a stray
> space in the property name. This breaks the build.

**Step 2 — Ask for the fix.** Type:

```
fix it
```

I edit the file directly. Nothing to copy, nothing to paste back.

**Step 3 — Save your work.** Type:

```
commit and push
```

Your fix is now on GitHub.

That's the entire loop: **check → fix → commit**. Everything else is a variation
on it.

---

## The five things you'll actually type

| You want | Type something like |
|---|---|
| Find a problem | `check src/App.jsx for bugs` |
| Fix a problem | `fix the syntax error in the analyzer` |
| Understand code | `explain what this component does` |
| Save your work | `commit and push` |
| See what changed | `what's different on this branch?` |

There's no special syntax to learn. Write it how you'd say it to a colleague.

---

## Two habits that make this work well

### 1. Name the file

| Weaker | Stronger |
|---|---|
| `fix my code` | `fix the analyzer component` |
| `it's broken` | `the form in src/Form.tsx won't submit` |

Naming the file skips a round of guessing.

### 2. Paste the whole error

Not just the last line — the whole thing, including the stack trace. It usually
names the exact file and line, which means I can go straight there.

```
TypeError: Cannot read properties of undefined (reading 'map')
    at ChargeList (src/components/ChargeList.jsx:42:18)
    at renderWithHooks (react-dom.development.js:14985:18)
```

That's enough for me to find and fix it without asking you anything.

---

## What I'll ask permission for

You can experiment freely. I stop and check with you before anything that's
hard to undo:

- Pushing or force-pushing to a remote
- Deleting files or branches
- Merging or closing pull requests
- Destructive git commands (`reset --hard`, `clean`, `checkout` over changes)
- Posting comments or anything else visible to other people

Reading files, searching, and making local edits happen without interruption —
those are all reversible with git.

---

## Where to go next

The [Cheat Sheet](./claude-code-cheatsheet.md) has the complete list: slash
commands like `/review` and `/security-review`, prompt patterns for tricky
debugging, and the full git and pull request workflow.

Stuck on something specific? Just describe it. No particular format needed.
