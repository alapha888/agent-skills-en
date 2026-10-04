# Draft: dev.to article #3

> Publishing notes (not part of the article):
> - Suggested title: "Meeting Minutes Your Agent Writes in 3 Buckets: Decisions, Actions, Open Questions"
> - Suggested tags: `claudecode`, `productivity`, `ai`, `meetings`
> - Cover: a screenshot of the minimal example below (raw notes -> structured minutes), or the skill folder structure.
> - Publish timing: at least one day after article #2 (published 2026-10-02 02:57 CST). Weekday morning US time. Publishing itself is done by the main agent in a logged-in dev.to session; this file is only the draft.
> - Word count target: 800–1200 for the article body (check with `wc -w` before publishing).
> - Grounding: every rule and the example below come verbatim from skills/meeting-notes/SKILL.md in this repo. No invented metrics, no hype.

---

# Meeting Minutes Your Agent Writes in 3 Buckets: Decisions, Actions, Open Questions

I pasted two pages of raw meeting notes into my coding agent and asked for minutes. What came back was a tidy chronological summary: who spoke first, what they said, who replied, what they said next. It read well. It was also useless — nobody could tell what the meeting had actually decided, and the three follow-ups mentioned in passing had no owners and no dates.

The problem was not the agent. "Write up the minutes" is a vibe, not a procedure. So I wrote the procedure down as a skill, and the agent has followed it since.

## The one rule that changes everything

Minutes are not a transcript with better formatting. They exist so that someone who missed the meeting can catch up in 3 minutes — and so attendees know exactly what they owe.

That means everything gets sorted into exactly three buckets:

- **Decisions** — one per line, phrased as "Decided to do X", never "Discussed X".
- **Action items** — each must have an owner and a deadline. No exceptions.
- **Open questions** — what is still undecided, what is blocking it, and who owns the next step.

And the whole thing opens conclusion-first: at most 3 lines on what the meeting decided, before any detail.

## The part agents get wrong: inventing the missing pieces

Raw notes are messy. "Draft the proposal by next Wednesday" — whose job is that? The notes don't say. A helpful-sounding agent will guess a name, or quietly drop the deadline, and the minutes become fiction with good formatting.

The skill forbids that, explicitly:

- If the notes name no owner, mark the item `[unassigned]`. If no deadline, mark `[TBD]`.
- Names, dates, and numbers that are not in the notes must not appear. Mark missing ones `[to confirm]`.
- No editorializing. Not "Maria's proposal seemed shaky" — only "Maria's proposal was rejected because…" and only if a reason was actually stated.

Marking a gap is more useful than hiding one. `[unassigned]` in the minutes is a to-do for the team; an invented owner is a bug nobody notices until the deadline passes.

## A minimal example

Input (raw notes excerpt):

```text
...James said the login page is too slow, Maria suggested adding a cache layer, everyone agreed it's worth a pilot; draft the proposal by next Wednesday; pricing strategy still open, invite Finance next time...
```

Output:

```markdown
## Meeting minutes (example)

**Bottom line**: Pilot a cache layer to speed up the login page; pricing strategy undecided, pending a session with Finance.

### Decisions
- Adopt a cache layer for login-page performance (pilot first, not a full rollout).

### Action items
- [ ] Maria: draft the caching proposal, due next Wednesday `[date to confirm]`
- [ ] [unassigned]: schedule pricing discussion with Finance `[time TBD]`

### Open questions
- Pricing strategy: no decision reached; the action-item owner will book a dedicated session with Finance.
```

Notice what the output refuses to do: it does not turn "next Wednesday" into a calendar date, and it does not assign the Finance meeting to whoever was mentioned last. The brackets are the honest part.

## Two more constraints that keep minutes honest

**Length control.** The minutes body must be at most 1/3 the length of the raw notes. Longer means the agent summarized instead of distilling — redo it. This single ratio kills most chronological bloat.

**Self-check before output.** Before returning anything, the agent verifies: does every action item have an owner? A deadline? Are decisions affirmative statements? Do open questions have a next step? Any "no" gets flagged in the output, not glossed over.

## The skill

This is one of five free, MIT-licensed skills in a small pack I maintain — the others cover commit messages, code review, technical-writing proofreading, and structured deep research. Each one is a single `SKILL.md` file: copy the folder into your agent's skills directory and it applies the workflow without being re-explained every session.

Repo: https://github.com/alapha888/agent-skills-en — the meeting-notes skill is under `skills/meeting-notes/`, including the full anti-pattern list (chronological minutes, ownerless action items, invented details, decisions written as discussion).

If your team has a different minutes format, fork the file and change the buckets. The format is the easy part; the discipline — conclusion first, owners or brackets, nothing invented — is the part worth keeping.
