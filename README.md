# Agent Skills — English Productivity Pack

[![skills.sh](https://skills.sh/b/alapha888/agent-skills-en)](https://skills.sh/alapha888/agent-skills-en)
<a href="https://aiagentslisting.com/agent-skills-en?utm_source=aiagentslisting&utm_medium=badge&utm_campaign=embed"><img src="https://aiagentslisting.com/agent-skills-en/badge.svg?theme=light" alt="Featured on AI Agents Listing" width="200" height="50" loading="lazy" /></a>

A small collection of agent skills for everyday knowledge-work tasks: proofreading technical docs, writing commit messages, turning meeting notes into minutes, reviewing code, and structuring deep research. Free to use, no sign-up.

> 中文用户：另有《Agent Skills 中文实战包》v1（5 个 skill 中文版 + 中文安装指南 + 3 个中文实战案例），¥9.90 起一次买断 → [爱发电购买](https://afdian.com/item/595000f4bd6011f1995a52540025c377)。本仓库英文原版永久免费（MIT）。

## Skills

| Skill | What it does |
|---|---|
| `tech-writing-proofread` | Proofreads English technical writing — typos, grammar, punctuation, terminology consistency, jargon, structure — and returns an itemized Original → Suggestion → Reason checklist without rewriting the document. |
| `git-commit-message` | Generates conventional-commit messages from staged changes: type prefix + imperative subject (≤50 chars) + optional body explaining *why*. |
| `meeting-notes` | Turns raw meeting notes into structured minutes: conclusion first, then decisions / action items / open questions; every action item gets an owner and a deadline. |
| `code-review-checklist` | Five-axis code review (correctness, security, readability, performance, test coverage) with actionable comments instead of style nitpicks. |
| `deep-research-framework` | Framework for deep research reports: define the question, tier sources, cross-verify, then write conclusion-first reports with explicit uncertainty statements. |

## How to use

Each skill lives in `skills/<name>/SKILL.md`. The `SKILL.md` file starts with a `name` and a `description` field — the description is written so agent frameworks can surface the skill when a matching request comes in.

To use a skill, tell your agent what you want to do (for example, "proofread this README" or "turn these notes into minutes"), and point it at the corresponding `SKILL.md` if it doesn't pick it up automatically. The agent then follows the workflow inside.

## Design principles

- **Checklists, not essays.** Every skill is a workflow the agent can execute step by step, with a minimal runnable example.
- **Proofread, don't rewrite.** The proofreading skill flags defects and suggests fixes; it never rewrites your voice away.
- **No fabrication.** The meeting-notes and research skills refuse to invent names, dates, or sources — missing information is marked, never guessed.
- **Actionable over exhaustive.** Code review is capped at 10 comments; a review drowning in trivia is worse than a short one that finds the real bug.

## License

MIT. Use them, fork them, adapt them — attribution appreciated but not required.

## Custom skill development

I take on custom skill / AI workflow commissions: a tailored skill for your team's recurring workflow (from ¥499), or a lightweight automation / landing-page build (from ¥999). Reach me via [Afdian DM](https://afdian.com/a/cb-alerts). After we agree on scope, the 30% deposit goes through [this Afdian listing](https://afdian.com/item/68b11b88bd5011f199ec52540025c377) (¥150 / ¥299 tiers).

## Agent Skills Pro

Need the advanced workflows? [Agent Skills Pro](https://alapha888.github.io/agent-skills-pro/) ($39 one-time) adds three paid skills — `multi-agent-decompose`, `codebase-map`, and `release-notes` — for coordinating parallel agents, onboarding onto unfamiliar repos, and cutting readable releases. The free pack above stays free.
