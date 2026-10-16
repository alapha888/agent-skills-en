# Draft: Hashnode article #1

> Publishing notes (not part of the article):
> - Title: "5 Production-Ready Skills for Your Coding Agent"
> - Suggested tags: `claude-code`, `ai-agents`, `developer-tools`, `productivity`
> - Canonical: two of the five skills were covered in depth earlier on dev.to; the article itself carries the attribution line at the top. If Hashnode's canonical-URL field is used, leave it empty — this combined guide has no single original.
> - Purpose: second English distribution surface for agent-skills-en (Hashnode SEO) and an eligible source for daily.dev pickup.
> - Grounding: every quoted rule is verbatim from the corresponding `skills/*/SKILL.md`; the two code examples are the examples shipped in those files. No invented metrics, no hype.
> - Drafting: one round via antigravity (Claude Sonnet 4.6 Thinking) + manual edits — see DEVNOTE at the end of this file.

---

# 5 Production-Ready Skills for Your Coding Agent

*Two of these skills — git-commit-message and code-review-checklist — were originally covered in depth on dev.to: [Teach Your Coding Agent to Write Commit Messages Your Team Will Actually Read](https://dev.to/alapha888/teach-your-coding-agent-to-write-commit-messages-your-team-will-actually-read-2fjp) and [Teach Your Coding Agent to Review Code Without the Style Nitpicks](https://dev.to/alapha888/teach-your-coding-agent-to-review-code-without-the-style-nitpicks-5mg). This post is the combined release guide for the full five-skill pack.*

---

Every developer who has worked with a coding agent for more than a day has run into this: you start a new session, the agent asks you to write a commit message, and you spend two minutes re-explaining your team's commit format — conventional commits, imperative subject, body explains why not how. Or you ask for a code review and get back a list of semicolon complaints. Or you paste meeting notes and the agent invents a name for the action item owner because you forgot to assign one.

These are recurring conventions, not one-off instructions. The right fix is to write each convention down once, in a file the whole team can version-control and share. That is what a skill does: a folder with a `SKILL.md` that your agent (Claude Code, Codex, Cursor, Gemini CLI, or any tool that reads from a skills directory) loads when the task matches. The file carries the workflow, the rules, the examples, and the anti-patterns. Once committed to the repo, every teammate's agent follows the same rules without any of them having to explain it again.

The pack below is free and MIT-licensed. Five skills, one repo: [github.com/alapha888/agent-skills-en](https://github.com/alapha888/agent-skills-en).

---

## 1. `git-commit-message`

**The pain:** Agents default to vague commit messages — `fix bug`, `update file`, `refactor`. Getting a useful message requires spelling out your format every time, and even then the agent often conflates the subject line with an explanation.

**What the skill does:** The agent follows a strict two-part structure. The subject is `type: imperative phrase`, capped at 50 characters. The body explains *why* the change was made, not how. Bug fixes must include the trigger condition. If the staging area is empty, the agent stops and asks rather than inventing a message from context.

> "The subject is for skimmers; the body is for future-you in three months. Keep the two jobs separate."

A real example the skill ships with:

```
git commit -m "fix: keep order-list filters across pagination" -m "Trigger: filter first, then turn the page. Cause: page turns dropped the query params."
```

**Install:** Clone the repo and copy `skills/git-commit-message` into `~/.claude/skills/` (global) or `.claude/skills/` inside your project.

---

## 2. `code-review-checklist`

**The pain:** Ask an agent to review a PR and you get a mix of real issues and style opinions — trailing spaces, quote style, indentation. The noise buries the signal, and team members learn to ignore agent reviews.

**What the skill does:** Reviews follow five axes in strict priority order: correctness, security, readability, performance, test coverage. Every comment is formatted as `[axis] file:line problem → suggested fix`. The review is capped at 10 comments. Diffs over roughly 400 lines are flagged for splitting before the review proceeds. Correctness and security issues are marked `Must fix`; the rest are `Should fix`.

> "No style policing: indentation, quotes, semicolons — that's the linter's job, not a human's."

A real example comment the skill ships with:

```
[Must fix][Correctness] order.py:87 empty order list triggers IndexError → guard for empty before taking [0]
```

**Install:** Copy `skills/code-review-checklist` into `~/.claude/skills/` or `.claude/skills/` in your project.

---

## 3. `meeting-notes`

**The pain:** Raw meeting notes are long and unstructured. Paste them into an agent and you typically get a bullet-point summary that buries the actual decisions, invents deadlines that were never mentioned, and assigns owners to action items that had none.

**What the skill does:** The output opens with the conclusion, then organizes everything into three buckets. Decisions are phrased as "Decided to do X" — never "Discussed X." Action items each carry an owner and a deadline; missing owners are marked `[unassigned]`, missing deadlines `[TBD]`. Open questions state what is blocking and who owns the next step. The final minutes are no longer than one third the length of the raw notes.

> "Do not fabricate. Names, dates, and numbers not in the notes must not appear; mark missing ones `[to confirm]`."

**Install:** Copy `skills/meeting-notes` into `~/.claude/skills/` or `.claude/skills/` in your project.

---

## 4. `deep-research-framework`

**The pain:** Agents are willing to write confident-sounding research reports full of numbers with no traceable source. You ask for a competitive analysis and get statistics that either come from a single blog post or cannot be verified at all.

**What the skill does:** Before searching, the agent writes the research question in one sentence. Sources are tiered before searching begins: primary sources are official docs, original papers, filings, and measured data; secondary sources are reputable press, industry reports, and expert interviews; tertiary sources — social posts, forum threads, aggregator sites — are leads only, never evidence. Key conclusions require two or more independent sources (two sources quoting the same origin do not count as independent). Reports open with conclusions and close with an explicit uncertainty statement. Every key fact is dated.

> "Every number in the report has a source. A number without a source is deleted, not rewritten."

**Install:** Copy `skills/deep-research-framework` into `~/.claude/skills/` or `.claude/skills/` in your project.

---

## 5. `tech-writing-proofread`

**The pain:** Ask an agent to proofread a README or doc and it rewrites the whole thing — changing the structure, rephrasing accurate but imperfect sentences, and occasionally "correcting" technical claims it does not fully understand.

**What the skill does:** The agent proofreads only, in one pass, across six specific categories: typos and spelling, grammar, punctuation, inline code and proper noun formatting, sentence style, and structure. The output is an itemized list in the format `Original → Suggestion → Reason`, followed by a short count of issues by category. Suspected factual errors are flagged `[verify]` and left as-is. The agent does not touch anything outside those six categories.

> "Fix language, not facts."

**Install:** Copy `skills/tech-writing-proofread` into `~/.claude/skills/` or `.claude/skills/` in your project.

---

## Install the Whole Pack

To add all five skills at once:

```bash
npx skills add alapha888/agent-skills-en
```

The pack is free and MIT-licensed — use it, fork it, or adapt it for your team's conventions.

A Pro pack with three additional skills is available for $39: [https://alapha888.github.io/agent-skills-pro/](https://alapha888.github.io/agent-skills-pro/)

---

## DEVNOTE (not part of the article — remove before publishing)

- Drafting record: one round with antigravity — `agy -p <brief>` with `--model "Claude Sonnet 4.6 (Thinking)"` (command exited 0). The brief contained the structure, style constraints, and verbatim rule excerpts from the five SKILL.md files. The agy draft came back at ~1,030 words, structurally complete, and was adopted with the edits below rather than rewritten.
- Edits made to the agy draft:
  1. `git-commit-message` example: agy had reformatted the shipped example with a shell line-continuation backslash; restored to the exact single-line form in `skills/git-commit-message/SKILL.md`.
  2. `deep-research-framework` source tiering: agy's paraphrase ("secondary sources are analysis of evidence") was looser than the source; replaced with the tier definitions from `skills/deep-research-framework/SKILL.md` (primary = official docs, original papers, filings, measured data; secondary = reputable press, industry reports, expert interviews; tertiary = social posts, forum threads, aggregator sites — leads only, never evidence).
- Checked in the agy draft and found clean (no changes needed): all five blockquote rules match SKILL.md word for word; both code examples are the real examples shipped in the SKILL.md files (no invented agent output); no efficiency or productivity numbers, no hype wording; per-skill install lines and the closing `npx skills add alapha888/agent-skills-en` command match the repo's actual layout.
