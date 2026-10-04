# Draft: dev.to article #5

> Publishing notes (not part of the article):
> - Suggested title: "Research Reports Your Agent Writes Need Sources Before Sentences"
> - Suggested tags: `research`, `ai`, `productivity`, `writing`
> - Cover: a screenshot of the report outline template below, or the skill folder structure.
> - Publish timing: at least one day after article #4. Weekday morning US time. Publishing itself is done by the main agent in a logged-in dev.to session; this file is only the draft.
> - Word count target: 800–1200 for the article body (check with `wc -w` before publishing).
> - Grounding: every rule and the outline template below come verbatim from skills/deep-research-framework/SKILL.md in this repo. No invented metrics, no hype.
> - Series note: this is the fifth and final article covering the five skills in the pack (commit messages / code review / meeting notes / proofreading / deep research).

---

# Research Reports Your Agent Writes Need Sources Before Sentences

Ask a coding agent for a research report and you usually get fluent prose first and evidence later — if at all. A single forum post becomes "research shows." A number from 2023 is presented as the current state. Twenty sources are listed at the end, and you still cannot tell what the author actually believes.

The failure is structural, not stylistic: the writing started before the question was defined and before the sources were tiered. So I wrote the workflow down as a skill, and the skill's first claim is blunt: the quality floor of research is set by its sources, not its prose.

## Step one: define the question before searching anything

The workflow starts with one sentence stating what the report must answer, plus at most three sub-questions. Starting before the question is clear guarantees the research will sprawl — the agent collects whatever it finds first and the report's shape is decided by search order instead of by the question.

## Step two: tier the sources before you believe them

Sources are tiered before searching, so you don't believe whatever you find first:

- **Primary**: official docs, original papers, original filings, protocol/legal texts, measured data.
- **Secondary**: reputable press, industry reports, expert interviews.
- **Tertiary**: social-media posts, forum threads, aggregator sites — leads only, never evidence.

That last line is a hard rule in the skill: no tertiary source supports a core conclusion. A forum thread can point a direction, never serve as evidence.

## Step three: cross-verify, and count independence honestly

Key conclusions need two or more independent sources. Two sources quoting the same origin don't count as independent — that is the trap that makes a single press release look like a consensus. If no second source exists, the conclusion is downgraded to a "single-source claim" and marked as such, instead of being quietly upgraded by confident wording.

Related rules:

- Every number in the report has a source. A number without a source is deleted, not rewritten.
- Date every key fact ("as of Sep 2026"). Undated information is treated as "possibly stale" by default.

## Writing structure: conclusion first, uncertainty last

Only after those three steps does writing start, and the structure is fixed:

- **Opening**: 3–5 lines stating the core conclusions.
- **Body**: one section per sub-question, each in "conclusion → evidence → sources" order.
- **Closing**: an uncertainty statement — what wasn't found, what's speculation, under what conditions the conclusions change.

The skill also insists on ordering inside the author's head: state "what you don't know" before "what you know" — honest uncertainty beats pretty certainty. And mark speculation as speculation: use "may", "likely", "unverified" — never dress speculation up with "clearly" or "it is well known".

The report outline template from the skill:

```markdown
# Research Report: <Topic> (example outline)

**Core conclusions** (3–5 lines): …

## 1. Sub-question one
- Conclusion: …
- Evidence: … (source: primary/secondary, as of …)
- Evidence: … (second independent source)

## 2. Sub-question two
…

## Uncertainty statement
- Not found: …
- Single-source claims: … (one source only, pending verification)
- Invalidation conditions: if … changes, conclusion X in this report needs reassessment.
```

## The anti-patterns are the point

The skill lists its own failure modes explicitly:

- Single-source verdicts: one social-media post becomes "research shows".
- Speculation as fact: "clearly" and "it is well known" are the most dangerous words in a research report.
- Undated facts: 2023 data presented as the current state; the conclusion quietly expires.
- Evidence pile with no conclusion: 20 sources listed, and the reader still can't tell what the author believes.
- Hiding the unknowns: burying what wasn't found makes the report look omniscient and plants landmines.

That last one is why the uncertainty statement is a required closing section rather than a footnote. A report whose unknowns are explicit can be trusted where it does claim something; a report that hides them cannot be trusted anywhere.

## The skill

This is one of five free, MIT-licensed skills in a small pack I maintain — the others cover commit messages, code review, meeting minutes, and technical proofreading. Each one is a single `SKILL.md` file: copy the folder into your agent's skills directory and it applies the workflow without being re-explained every session.

Repo: https://github.com/alapha888/agent-skills-en — the research skill is under `skills/deep-research-framework/`, including the full workflow and anti-pattern list.

If your work has house rules of its own — sources you always trust or never cite — fork the file and add them to the tiering step. The structure is the stable part; the source list is yours.
