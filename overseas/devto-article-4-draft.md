# Draft: dev.to article #4

> Publishing notes (not part of the article):
> - Suggested title: "Proofreading Is Not Rewriting: A Checklist Skill for Technical Docs"
> - Suggested tags: `writing`, `documentation`, `ai`, `productivity`
> - Cover: a screenshot of the minimal example below (input snippet -> checklist), or the skill folder structure.
> - Publish timing: at least one day after article #3 (published 2026-10-03 03:53 CST). Weekday morning US time. Publishing itself is done by the main agent in a logged-in dev.to session; this file is only the draft.
> - Word count target: 800–1200 for the article body (check with `wc -w` before publishing).
> - Grounding: every rule and the example below come verbatim from skills/tech-writing-proofread/SKILL.md in this repo. No invented metrics, no hype.

---

# Proofreading Is Not Rewriting: A Checklist Skill for Technical Docs

I asked my coding agent to proofread a README draft. It returned a beautifully rewritten document — smoother sentences, tidier structure, my voice completely gone. Two of its "fixes" also quietly changed technical statements into things that were no longer true.

That is the standard failure mode of "AI polish": the model treats proofreading as a license to rewrite, and rewriting a technical document without understanding it is how factual errors get introduced by the tool that was supposed to catch them.

So I wrote the boundary down as a skill. The agent now proofreads. It does not rewrite.

## Rule zero: fix language, not facts

The skill's first rule is the one that prevents the damage above:

- Fix language, not facts. A suspected factual error becomes `[verify] This contradicts the usual definition — please confirm`, never a silent "correction."
- Do not rewrite whole paragraphs. Even a wordy paragraph gets only specific, fixable sentences flagged; keep the author's voice.
- One pass only. The deliverable is a "no-defects" checklist, not a perfect text.

If the agent is unsure whether something is a typo or a deliberate technical choice, it marks the item `[verify]` instead of forcing a change. A flagged question is useful; a confident wrong edit is a bug.

## Six categories, and nothing outside them

Unbounded proofreading drifts into "is this paragraph well written," which is taste, not defects. The skill checks paragraph by paragraph, but only for six categories:

- **Typos and spelling**: transposed letters, doubled words ("the the"), commonly confused pairs ("affect/effect", "its/it's", "complement/compliment").
- **Grammar**: subject-verb agreement, verb tense consistency within a procedure, dangling modifiers, missing articles before singular countable nouns.
- **Punctuation**: consistent serial (Oxford) comma usage; hyphens in compound adjectives ("command-line tool"); no double spaces after periods; consistent use of em dashes vs parentheses.
- **Inline code and proper nouns**: commands, file names, and paths in backticks; proper nouns in their official casing (`GitHub`, not `github`; `JavaScript`, not `Javascript`).
- **Sentence style**: prefer active voice ("The system calls the function" over "The function is called by the system"); cut filler ("basically", "simply", "just", "very"); one idea per sentence.
- **Structure**: headings in parallel form; lists use parallel items; steps in a procedure are imperative and numbered; acronyms are expanded on first use.

Two steps happen before the paragraph pass: read the whole document once to identify its type (tutorial / API reference / blog post / README — tutorials tolerate a conversational voice, API references must be precise), and build a terminology list, because one concept named several ways ("callback" vs "callback function", "sign in" vs "log in") is the defect readers actually trip over. The list standardizes on the most frequent form.

## The output is a checklist, not a new document

Every item comes back as "Original → Suggestion → Reason", with line numbers or short quotes, and the pass closes with statistics: N items total, broken down by category, so the author sees the distribution at a glance and decides what to accept.

The minimal example from the skill, on one genuinely messy sentence:

Input:

```text
This function will be called by the system after the data is ready, you can use it to basically handle the registration of the callback, the timeout is 5 s, examples on github can be referenced.
```

Output:

```text
1. [Style] "will be called by the system" → "the system calls" (passive → active)
2. [Style] "basically handle" → "handle" (cut filler word)
3. [Terminology] "callback" — if written elsewhere as "callback function", unify on one form (most frequent wins)
4. [Grammar] run-on sentence: split after "ready." into two sentences
5. [Proper noun] "github" → "GitHub" (official casing)

Statistics: 5 items — style 2, terminology 1, grammar 1, proper noun 1.
```

Notice what the output refuses to do: it does not merge the findings into a polished replacement paragraph. The author keeps control of every change, and can reject any single item without losing the rest.

## The anti-patterns are the point

The skill lists its own failure modes explicitly:

- Turning proofreading into rewriting: tearing a paragraph down so the author's voice and structure are lost.
- Hallucinated "corrections": changing an uncertain technical statement as if it were a typo, introducing a factual error.
- Typos-only checks: inconsistent terminology and sloppy structure are the real defects in technical docs.
- Endless iteration: the user says "polish it once more" and it never ends — the deliverable is the checklist, not a perfect text.

That last one matters more than it sounds. "One pass only" is a stopping rule, and stopping rules are what make an agent workflow usable instead of a loop you supervise forever.

## The skill

This is one of five free, MIT-licensed skills in a small pack I maintain — the others cover commit messages, code review, meeting minutes, and structured deep research. Each one is a single `SKILL.md` file: copy the folder into your agent's skills directory and it applies the workflow without being re-explained every session.

Repo: https://github.com/alapha888/agent-skills-en — the proofreading skill is under `skills/tech-writing-proofread/`, including the full workflow and anti-pattern list.

If your docs have house rules of their own — a preferred term list, a casing table — fork the file and add them to the terminology step. The categories are the stable part; the word list is yours.
