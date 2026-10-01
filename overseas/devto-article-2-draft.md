# Draft: dev.to article #2

> Publishing notes (not part of the article):
> - Suggested title: "Teach Your Coding Agent to Review Code Without the Style Nitpicks"
> - Suggested tags: `claudecode`, `codereview`, `productivity`, `ai`
> - Cover: a screenshot of a 4-comment review in the fixed `[axis] file:line` format, or the skill folder structure.
> - Publish timing: at least one day after article #1 (new account: one post per day). Weekday morning US time.
> - Word count target: 800–1200 for the article body (check with `wc -w` before publishing).

---

# Teach Your Coding Agent to Review Code Without the Style Nitpicks

I asked my coding agent to review a 120-line pull request last month. It came back with 23 comments. Eighteen were about quote style, line length, and import order. It missed the SQL query built by string concatenation. It missed the database call inside the loop.

The review was technically thorough and completely useless. The dangerous stuff sailed through while the agent graded my taste in quotation marks.

That was the day I wrote down how I actually want code reviewed — and turned it into a skill the agent follows every time.

## The review that got it wrong

Here's the kind of diff I'm talking about — a small Python helper, the sort of thing that shows up in every PR:

```python
def process_orders(orders, db):
    results = []
    for order in orders:
        user = db.query("SELECT * FROM users WHERE id = " + str(order.user_id))
        results.append({
            "id": order.id,
            "total": order.total,
            "processed_at": int(time.time()) + 86400,
        })
    return results[0]["total"]
```

A free-form agent review of this tends to produce: "consider using double quotes consistently," "this function could use a docstring," "line 4 exceeds 88 characters." Meanwhile `results[0]["total"]` throws an `IndexError` on an empty order list, the user id is concatenated into raw SQL, and `db.query` runs once per order inside the loop. The three things that would page someone at 2am get outvoted by formatting opinions.

The problem isn't that the agent can't review code. It's that "review this code" is a vibe, not a procedure. Every session invents its own definition of what matters. So I wrote the definition down.

That's what an agent skill is: a `SKILL.md` file — frontmatter plus a step-by-step workflow — that lives in your agent's skills directory. When you ask the agent to do a matching task, it reads the skill and follows it. No re-prompting, no drift. (If you want the full version of this idea, my first post walks through the same pattern for commit messages.)

## Five axes, in order

The skill — `code-review-checklist` — reduces a review to one question: "Will this code become someone else's problem within three months?" Then it walks five axes in priority order:

1. **Correctness** — edge cases (null, empty, zero, negative, oversized), concurrency and timing assumptions, swallowed exceptions. The only axis that can block a merge.
2. **Security** — user input concatenated into SQL, shell, or HTML; hard-coded secrets; sensitive data in logs.
3. **Readability** — names that say what things are, one job per function, no magic numbers. Flag only what you genuinely can't understand — not "I'd write it differently."
4. **Performance** — repeated queries or recomputation inside loops, N+1 problems, avoidable copies of large objects. No data-free speculation: "this might get slow" is not a comment.
5. **Test coverage** — new logic has tests, edge cases have cases. All-green tests with the critical path uncovered still get sent back.

Three guardrails keep the review honest. **Scope first**: over ~400 changed lines, the agent asks for a split — review quality on huge diffs always collapses, and pretending otherwise produces theater. **At most 10 comments**: more than that means the code needs a rewrite, not fifty line-items of grading. **No style policing**: indentation, quotes, semicolons — that's the linter's job, and the skill says so explicitly.

Every comment has a fixed format — `[axis] file:line problem → suggested fix` — and every comment must cite a concrete line. A comment without a code reference is invalid by definition. Then triage: `Must fix` (correctness, security) blocks the merge; `Should fix` (readability, performance, tests) doesn't, but the agent says so out loud instead of leaving you to guess which is which.

## The same diff, after

Run the skill over that `process_orders` function and you get something like this:

```text
[Must fix][Correctness] orders.py:9  empty orders list triggers IndexError → guard for empty before taking [0]
[Must fix][Security] orders.py:4  user id concatenated into SQL string → use parameterized query
[Should fix][Performance] orders.py:4  db.query inside the loop (N+1) → batch-fetch users before the loop
[Should fix][Readability] orders.py:7  magic number 86400 → name it SECONDS_PER_DAY
```

Four comments, all actionable, all pointing at lines. No quote-style opinions. The merge-blocking ones are labeled as such. This is what I wanted from a review all along: not a second pair of eyes grading my style, but a checklist that catches the 2am-paging stuff before it merges.

## Install and use

Same pattern as the other skills — a folder you copy:

```bash
git clone https://github.com/alapha888/agent-skills-en.git
cp -r agent-skills-en/skills/code-review-checklist ~/.claude/skills/
```

No dependencies, no network calls, no sign-up. Then: "Review this diff." The agent reads the skill and follows the axes. If you want the whole team on it, commit the folder to `.claude/skills/` in the repo — now every review in the project runs the same checklist. The format is an open standard, so this isn't Claude-only; the same folder works in Codex, Cursor, Gemini CLI, and other hosts that support skills.

## The copyable core

If you'd rather write your own, the heart of the skill is this checklist — the minimal executable version you can paste into your own `SKILL.md`:

```markdown
## Code review checklist

- [ ] Correctness: edge cases (null/0/negative/oversized) handled, exceptions not swallowed
- [ ] Correctness: concurrency/timing assumptions hold, no races
- [ ] Security: no SQL/shell/HTML injection points, no hard-coded secrets, no sensitive data in logs
- [ ] Readability: names are descriptive, functions have a single responsibility, no magic numbers
- [ ] Performance: no repeated queries/computation in loops, no N+1, no evidence-free performance worries
- [ ] Tests: new logic is covered, edge cases have cases
- [ ] Scope: diff ≤ ~400 lines, otherwise split first
```

Plus the two rules that do most of the work: every comment cites a line, and style stays with the linter. Everything else is commentary.

## What it can't fix

The skill won't save you from a 2,000-line diff — it will just ask you to split it, every time, until you do. It won't catch architectural mistakes, because a checklist reviews code, not design: if the whole approach is wrong, no axis flags it. And it inherits your tests' blind spots — if the critical path has no test and the reviewer (you) doesn't notice, the checklist can't notice for you. It's a mirror for your standards, not a replacement for judgment.

But for the everyday case — a normal-sized PR, written in a hurry, reviewed at the end of the day — it turns "review this" from a vibe into a procedure. The dangerous stuff gets caught, the nitpicks go to the linter, and the author gets four comments instead of twenty-three.

---

The code review skill is one of five I published — the set also covers commit messages, proofreading docs, meeting notes, and deep-research reports. All free, MIT licensed, same install pattern: [github.com/alapha888/agent-skills-en](https://github.com/alapha888/agent-skills-en)

If you try it on a real PR, I'd like to know which axis fires most often for your codebase. Mine is readability, which tells me something about how I write code at 11pm.
