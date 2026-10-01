# Overseas Distribution Kit — agent-skills-en

Prepared 2026-10-01. Research + drafting only; nothing registered or published.
Repo: https://github.com/alapha888/agent-skills-en (MIT, default branch `master`, 0 stars as of 2026-10-01)

---

## Part A — 10 distribution targets

Ordered by readiness. Items marked ⏳ have an explicit gate; submit when eligible.

### Awesome lists (PR)

**1. ComposioHQ/awesome-claude-skills** — https://github.com/ComposioHQ/awesome-claude-skills
- Method: PR (submitted 2026-10-01 as **#2059**, awaiting review)
- Category fit: Productivity & Organization
- Notes: ~1.6k stars. Entry already placed per their format.

**2. sickn33/agentic-awesome-skills** — https://github.com/sickn33/agentic-awesome-skills
- Method: PR (submitted 2026-10-01 as **#1741**, awaiting review)
- Category fit: the repo holds each skill as a folder with extended frontmatter; all 5 skills validated locally before submitting.

**3. heilcheng/awesome-agent-skills** — https://github.com/heilcheng/awesome-agent-skills
- Method: PR (ready to send now)
- Category fit: "Community Skills → Productivity and Collaboration"
- Notes: 6.2k stars, MIT, not a fork, multilingual (EN/ZH/JA/KO/ES), has CONTRIBUTING.md. High-quality bar — emphasize the five-skill pack is one entry.

**4. uizze/awesome-agent-skills** — https://github.com/uizze/awesome-agent-skills
- Method: PR (ready to send now)
- Category fit: "Collections" section (lists other skill collections)
- Notes: smaller list (~50 stars), lower bar; good early win.

**5. travisvn/awesome-claude-skills** — https://github.com/travisvn/awesome-claude-skills ⏳
- Method: PR (deferred)
- Gate: repo requires **≥10 GitHub stars** (currently 0)
- Entry format (per their CONTRIBUTING): `- ** [agent-skills-en](url) ** - one-line description` under "Collections & Libraries"
- Notes: maintainer also states AI-generated submissions are not accepted — submit manually, not via agent automation.

**6. hesreallyhim/awesome-claude-code** — https://github.com/hesreallyhim/awesome-claude-code ⏳
- Method: **web issue form** (not PR — maintainer takes new-resource submissions as issues)
- Gate: first commit must be ≥14 days old (**eligible 2026-10-15**) or repo ≥100 stars
- Notes: maintainer explicitly forbids bot/gh-CLI submissions; submit by hand through the web form.

**7. VoltAgent/awesome-agent-skills** — https://github.com/VoltAgent/awesome-agent-skills ⏳
- Method: PR (deferred — longest gate)
- Gate: CONTRIBUTING explicitly rejects brand-new skills: *"Brand new skills that were just created are not accepted. Give your skill time to mature and demonstrate actual usage first."*
- Entry format (when eligible): `- ** [alapha888/agent-skills-en](url) ** - ≤10-word description`, appended to "Community Skills → Productivity and Collaboration"; PR title `Add skill: alapha888/agent-skills-en`
- Notes: 35k stars — the biggest list in the niche; worth the wait. Revisit after the repo has real usage (dev.to article traffic, other-list pickups).

### Devtools directories (web form / PR)

**8. AlternativeTo** — https://alternativeto.net
- Method: web form — "Suggest new application"
- Notes: account required to submit; per 2026 sources, new accounts face roughly a one-week submission cooldown. After the listing is live, use "Suggest as alternative" on related listings (e.g., alternatives to popular prompt libraries) to build inbound links.

**9. OpenAlternative** — https://openalternative.co/submit
- Method: web form
- Notes: open-source software directory. Approved entries are also picked up by the GitHub list piotrkulpinski/open-source-alternatives (auto-synced), so one submission yields two placements.

**10. DevHunt** — https://devhunt.org
- Method: GitHub PR (submissions via PR; community voting after acceptance)
- Notes: dev-tools launchpad. Consider timing the PR with the dev.to article publish so voters have something to read.

### Bonus — no submission needed (auto-indexed)

- **SkillsMP** (skillsmp.com) — automatically indexes skill repos on GitHub. No action; visibility grows as stars grow.
- **skills.sh** (Vercel leaderboard) — auto-tracks popular skill repos. No action.
- **LibHunt** (libhunt.com/site/project_submit) — web form, optional 11th target if more directory coverage is wanted.

---

## Part B — Product Hunt copy

> Draft only. Launch timing and assets (logo, screenshots, demo video) still to prepare.

**Tagline (49 chars):**
Five free agent skills for everyday knowledge work

**Description:**
Agent Skills — English Productivity Pack is five markdown files that teach your coding agent to do the tasks you keep re-explaining: proofreading docs without rewriting your voice, writing conventional commit messages, turning meeting notes into minutes, running five-axis code reviews, and structuring deep-research reports.

Each skill is a SKILL.md with a workflow, a minimal runnable example, and anti-patterns. Copy a folder into ~/.claude/skills and it works — no dependencies, no sign-up, no network calls. MIT licensed.

Works with Claude Code, Codex, Cursor, Gemini CLI, and any host that supports the open skills format.

**Maker's first comment:**
Hi, I'm the maker. I use Claude Code every day, and I got tired of typing the same instructions every week — how I want a doc proofread, what a good commit message looks like, how meeting notes should become minutes. So I wrote each workflow down once, as a skill, and stopped repeating myself.

These started as a Chinese-language pack I use daily; I rewrote every example for English workplace context rather than translating. They're free and MIT — take them, fork them, tell me where the workflows are wrong. I'll be here answering questions all day.

---

## Part C — Suggested order of operations

1. **Now (no gate):** send PRs to heilcheng (#3) and uizze (#4); set up AlternativeTo + OpenAlternative accounts and submit (#8, #9); prepare DevHunt PR (#10).
2. **Publish** the dev.to article (draft in `devto-article-draft.md`) — gives lists and voters something to read.
3. **On eligibility:** travisvn (≥10 stars), hesreallyhim (2026-10-15), VoltAgent (after real usage demonstrated).
4. **Later:** Product Hunt launch once the repo has initial traction + screenshots/demo prepared.
