# Draft: dev.to article

> Publishing notes (not part of the article):
> - Suggested title: "Teach Your Coding Agent to Write Commit Messages Your Team Will Actually Read"
> - Suggested tags: `claudecode`, `git`, `productivity`, `ai`
> - Cover: terminal screenshot showing a generated commit message, or the repo's skill folder structure.
> - Publish timing: weekday morning US time performs best on dev.to.
> - Word count target: 1500–2000. (Check with `wc -w` before publishing.)

---

# Teach Your Coding Agent to Write Commit Messages Your Team Will Actually Read

Every team's git history has them. `fix stuff`. `wip`. `update code`. `asdf`. Messages that made sense at 11pm on a Friday and mean nothing by Monday.

I use Claude Code every day, and for months my fix was the same as everyone's: I'd sigh, type out my commit conventions *again* in the prompt — conventional commits, imperative mood, short subject, explain the why in the body — and hope the agent remembered. It mostly worked. Until it didn't, because every session started from zero and every phrasing of my instructions produced a slightly different result.

The actual problem isn't that agents can't write good commit messages. It's that my expectations lived in my head, re-typed slightly differently each time. What I needed was to write the workflow down once, in a form the agent would follow the same way every time.

That's what an agent skill is: a `SKILL.md` file — frontmatter plus a step-by-step workflow — that lives in your agent's skills directory. When you ask the agent to do a matching task, it reads the skill and follows it. No re-prompting, no drift.

I ended up writing five of these for the repetitive knowledge-work tasks I kept re-explaining (proofreading docs, commit messages, meeting notes, code review, research reports). This post is about one of them — the commit message skill — because it's the smallest one to install and the easiest to feel the difference from. Ten minutes, and your whole team gets consistent messages.

## Why a skill, not a saved prompt?

You might wonder why this needs to be a "skill" at all instead of a text snippet you paste, or a paragraph in your project's `CLAUDE.md`. I tried all three, and they fail differently.

A pasted prompt works but resets every session. You're still the human linter, noticing when the agent drifted from your convention and correcting it. `CLAUDE.md` instructions are better — they're loaded automatically — but they compete with everything else in that file for the agent's attention, and they tend to grow into a junk drawer of project lore. A slash command is closer, but commands are usually about *doing* something specific ("run the deploy script"), not about *how to think through* a recurring judgment call.

A skill sits in the middle: it loads only when the task matches, it carries the full workflow (rules, examples, anti-patterns) instead of a one-line instruction, and it lives in a directory your whole team shares. The mental model that finally clicked for me: a saved prompt is a reminder to yourself; a skill is a checklist for the agent.

## Step 1: Install the skill

The skill is a single folder. Clone the repo and copy that folder into your agent's skills directory:

```bash
git clone https://github.com/alapha888/agent-skills-en.git
mkdir -p ~/.claude/skills
cp -r agent-skills-en/skills/git-commit-message ~/.claude/skills/
```

That's the entire install. No dependencies, no network calls, no sign-up. The skill is a markdown file; the agent reads it like a human would read a checklist.

If you want the whole team on the same conventions, put it at the project level instead: copy the folder to `.claude/skills/` in your repo and commit it. Now everyone who opens the project — and every agent session in it — follows the same workflow. The project layout looks like this:

```
your-repo/
├── .claude/
│   └── skills/
│       └── git-commit-message/
│           └── SKILL.md
├── CONTRIBUTING.md
└── ...
```

One line in your `CONTRIBUTING.md` and the convention is documented, versioned, and enforced by default rather than by nagging:

```markdown
## Commit messages

Commit messages are written with the `git-commit-message` skill
(`.claude/skills/git-commit-message/`): `type: imperative subject` ≤ 50 chars,
body explains the *why*. Don't hand-write them from memory — let the agent do it.
```

The format is an open standard, so this isn't Claude-only. The same folder works in Codex, Cursor, Gemini CLI, and other hosts that support skills.

## Step 2: Understand what the skill actually does

Before trusting it, read the workflow. It's short, and knowing what's inside is the difference between using a skill and cargo-culting one. Here's what the skill instructs the agent to do:

1. **Look at the real changes first.** Run `git status --short` and `git diff --cached --stat`. If the staging area is empty, stop and ask the user — never invent a commit message out of nothing.
2. **Pick exactly one type prefix** from `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, based on the diff. If one commit mixes types, the agent asks you to split it instead of papering over the mess.
3. **Write the subject** as `type: imperative phrase`, 50 characters max, starting with a verb: "Add…", "Fix…", "Remove…", "Unify…". Empty subjects like "update code" or "fix bug" are banned by name.
4. **Write the body** (1–3 lines) explaining *why*, not *how*. Bug fixes must state the trigger conditions. The diff already shows what changed line by line; the body is for the person reading this in three months.
5. **Output a ready-to-run command**, not bare text you have to assemble yourself.

Two design decisions in there are worth noticing. First, the subject is for skimmers and the body is for future-you — the skill keeps those two jobs separate instead of blending them. Second, there's no meta-commentary allowed: no "generated by AI" footers, no praise. The message is about the change, nothing else.

## Step 3: Use it on a real commit

Let's walk through a concrete example. Say you've staged a change that adds rate limiting to your login endpoint. Without the skill, you'd get whatever the agent feels like — maybe `fix login stuff`, maybe a three-paragraph essay. With the skill installed, you just say:

> Write a commit message for my staged changes.

The agent reads the staged diff, sees it's a new behavior (not a bug fix, not a refactor), and produces:

```bash
git commit -m "feat: add rate limiting to login endpoint" -m "Blocks brute-force attempts; limit is 5 tries per minute per IP, returns 429."
```

Type prefix, imperative subject under 50 characters, body that explains the *why* (brute-force protection) and the key behavior (5/min/IP, 429) — the two things you'd want to know without opening the diff.

Here's a bug-fix example, where the skill's "state the trigger conditions" rule earns its keep:

```bash
git commit -m "fix: keep order-list filters across pagination" -m "Trigger: filter first, then turn the page. Cause: page turns dropped the query params."
```

"Trigger: filter first, then turn the page" is the kind of sentence that saves someone twenty minutes of reproduction six months from now. Nobody writes that sentence unless a checklist tells them to.

## Step 4: What it refuses to do (and why that matters)

A skill is as defined by its refusals as its instructions. This one has four I like:

- **Empty staging area?** It stops and asks. It will not write a commit message from vibes.
- **Mixed commit?** A feature plus a refactor becomes two commits. The skill won't let one `feat:` subject cover both.
- **Catch-all `chore`?** Labeling everything `chore` until the type system means nothing is called out as an anti-pattern.
- **Novel-length subject?** `feat: add a really useful feature that greatly improves the user experience` gets flagged — the subject says *what*, praise is the user's job.

These sound obvious written down. That's the point: obvious, written down, followed every time, beats clever, in-your-head, followed sometimes.

## What the skill can't fix

Honest caveat: no skill fixes bad commit *hygiene*. If your habit is to `git add -A` the entire afternoon's work and ask for one message, the skill will correctly refuse to split it for you — it can ask you to stage things separately, but it can't decide what belonged together. The skill assumes you stage deliberately (per feature, per fix) and does the wording. Garbage in, slightly better-worded garbage out.

Similarly, the body explains *why* only if you can articulate why. When the agent asks "why did you make this change?", "because the ticket said so" is a sign the commit probably shouldn't exist in that form. The skill is a mirror for your process, not a replacement for it.

## Where this goes from here

The commit message skill is the smallest of the five I published — the full set also covers proofreading technical docs (itemized checklist, never rewrites your voice), turning meeting notes into minutes (every action item gets an owner and a deadline), five-axis code review (capped at 10 actionable comments, no style nitpicks), and structuring deep-research reports (explicit uncertainty statements). All free, MIT licensed, same install pattern: copy a folder, use it.

They started as a Chinese-language pack I use daily; I rewrote every example for English workplace context rather than translating. If your team has the same five repetitive workflows I did, they're yours to take: [github.com/alapha888/agent-skills-en](https://github.com/alapha888/agent-skills-en)

One last thing: the pattern generalizes. Any task you find yourself re-explaining to an agent weekly — a report format, a review checklist, a translation convention — is a skill waiting to be written down. A `SKILL.md` is just frontmatter (name, description) plus a workflow with one runnable example and a short anti-pattern list. Write the first one for the task that annoys you most; the rest get easier.

And if you try the commit message skill, I'd genuinely like to know where its workflow is wrong for your team. The fastest way to improve a checklist is to watch someone trip over it.
