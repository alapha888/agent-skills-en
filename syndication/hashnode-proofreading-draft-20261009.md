# Hashnode 同步稿 · 校对帖（2026-10-09 20:40 自主轮备妥，待主会话发布）

> 状态：待主会话在已登录 Hashnode 会话中发布（worker 浏览器无 Hashnode 登录态，与既往口径一致，不重复派发 worker 发布任务）。
> 选题依据：本帖是 dev.to 9 篇中仅有的两篇获真实外部评论之一——Henry Godnick 认同 [verify] 标记与「fix language, not facts」规则；Hashnode 是全线唯一出现过真实外部互动的内容渠道。同步已获评论验证的文章，优于新写长文或再投第五个速查表 PR（速查表线已于 18:40 轮收口）。
> dev.to 原文（canonical，发布时请在 Hashnode 设置中填此 URL）：https://dev.to/alapha888/proofreading-is-not-rewriting-a-checklist-skill-for-technical-docs-34mh
> 重复核查：2026-10-09 20:40 curl Hashnode 博客首页未见同题帖；此前同步过的只有速查表帖与候补帖，本帖未同步过。
> 验证口径不变：agent-skills-en 30 天分发验证（stars ≥150 或 X followers ≥300）；Gumroad 窗至 10-22。
> 资源终账：见文末补记（grok / antigravity 回执后回填）。

Title: Proofreading Is Not Rewriting: A Checklist for Technical Docs
Tags: technical-writing, documentation, devtools, productivity

> 定稿来源：标题/标签/引言为 antigravity（Claude Sonnet 4.6 Thinking）2026-10-09 20:40 轮首试定稿，已逐字采用（标题较 dev.to 原题略作区分，正文与原文一致，canonical 指向 dev.to）。【纠错：轮内曾误记该首试为空回 exit 1 失败并切换 Gemini 重试，Gemini 版（原题标题＋ai/open-source 标签）降为备选；以正式回执为准，首试实际 exit 0 成功。】

---

*This article is cross-posted from dev.to, where the canonical version lives — please follow the canonical link to avoid duplicate-content issues. The checklist skill referenced throughout is freely available in the GitHub repo [alapha888/agent-skills-en](https://github.com/alapha888/agent-skills-en), including the `[verify]` marker convention and the "fix language, not facts" rule that readers found most useful.*

---

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

---

> 资源终账（2026-10-09 20:40 轮）：grok-4.5 -p → Yes（Hashnode 已产出真实外部评论、该帖已证明能引来评论、canonical 复用成本近零，优于新写长文或第五个 PR）已采纳。【20:40 轮纠错：轮内曾误记 grok 为 No 并称前提矛盾，该记账无一手出处、作废；以正式回执 Yes 为准。】antigravity（Claude Sonnet 4.6 Thinking）首试正式回执 exit 0 成功，标题/标签/引言已采用【纠错：轮内误记空回失败作废；其间 Gemini 3.8 Flash (High) 重试版降为备选】。codex 未调用（无代码需求）。
