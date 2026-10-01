# agent-skills-en 海外分发调研 + 物料（2026-10-01）

> 只调研 + 写草稿，未做任何发布动作。发布前需复核。
> 注意：本机环境 reddit.com 被策略屏蔽，Reddit 规则来自 2026-09 的二手来源（多份独立交叉），发帖前必须对照 live 规则再验一次。

仓库：https://github.com/alapha888/agent-skills-en（5 个 skill，MIT，免费）

---

## 一、Awesome 列表：4 个目标（3 个可投，1 个缓投，1 个门槛未达）

### 1. ComposioHQ/awesome-claude-skills ✅ 现在可投

- 地址：https://github.com/ComposioHQ/awesome-claude-skills
- 规模：~76k stars，默认分支 `master`，PRs Welcome。
- 贡献流程（CONTRIBUTING.md，2026-10-01 已核验）：
  1. Fork → 建分支 `git checkout -b add-english-productivity-pack`
  2. 在 README 合适分类下加条目（分类：Productivity & Organization 最贴；单 skill 也可进 Communication & Writing / Development）
  3. PR 标题：`Add [Skill Name] skill` → 本次用 `Add English Productivity Skill Pack`
  4. PR 描述必须写：解决什么真实问题、谁在用这个 workflow、attribution、用法示例。
- 条目格式（跟随站内已有外部条目风格）：
  `- [Agent Skills — English Productivity Pack](https://github.com/alapha888/agent-skills-en) - Five free MIT skills for everyday knowledge work: proofreading docs, commit messages, meeting minutes, code review, deep-research reports. *By [@alapha888](https://github.com/alapha888)*`
- 建议放 `### Productivity & Organization`，按字母序插入。
- 无明示 star 门槛，但 76k 列表审核严，描述必须克制、写清真实用例。

### 2. sickn33/agentic-awesome-skills（原 antigravity-awesome-skills）✅ 现在可投

- 地址：https://github.com/sickn33/agentic-awesome-skills
- 规模：~47k stars，2600+ skills，一键安装生态，默认分支 `main`。
- 贡献模型（CONTRIBUTING.md，2026-10-01 已核验）：**不是加链接**，而是把 skill 文件夹直接贡献进 `skills/` 目录：
  1. Fork → `mkdir -p skills/<name>`，每个 skill 一个文件夹
  2. 每个 SKILL.md 需按他们的扩展 frontmatter 改写（含 `category / risk: safe / source: community / source_repo: alapha888/agent-skills-en / source_type: community / date_added / author / tags / tools`）
  3. 本地跑 `npm run validate`（或 `python3 tools/scripts/validate_skills.py`）
  4. PR 保持 source-only：**不要**带 `CATALOG.md`、`skills_index.json`、`data/*.json` 等生成物
  5. Commit 信息格式：`feat: add <skill> for [purpose]`
  6. 触碰 SKILL.md 的 PR 会触发自动 `skill-review` workflow；自动检查通过仍需人工复核逻辑。
- 工作量：5 个 skill = 5 个文件夹 + frontmatter 改写 + 本地 validate。建议一个 PR 打包 5 个（同一 pack，内聚）。
- 无明示 star 门槛。

### 3. travisvn/awesome-claude-skills ⏳ 门槛未达（≥10 stars 才收）

- 地址：https://github.com/travisvn/awesome-claude-skills
- 规模：~15k stars，默认分支 `main`，有 "Collections & Libraries" 分区（正适合 pack 形态）。
- 条目格式：`- ** [agent-skills-en](https://github.com/alapha888/agent-skills-en) ** - Free MIT pack of 5 English productivity skills for coding agents: proofreading, commit messages, meeting notes, code review, deep research`
- PR 标题示例：`Add English productivity skill pack`；一次只交一项。
- ⚠️ **硬门槛**：skill 需有 ≥10 GitHub stars，否则 PR 会被自动关闭。本仓库刚发布（0 stars），**先攒 star，达标后再投**。
- ⚠️ **反 AI 提交条款**：PR 不得由 AI 生成/提交，提交者必须在 PR 中明确承认人工撰写。建议由阿发本人点提交，或 PR 正文加人工署名声明（见第四节文案）。

### 4. hesreallyhim/awesome-claude-code ⏳ 门槛未达（14 天或 100 stars）

- 地址：https://github.com/hesreallyhim/awesome-claude-code
- 规模：~55k stars。
- ⚠️ **硬门槛**：资源需「首 commit ≥14 天且有持续开发」**或** ≥100 stars，否则自动关闭。本仓库 2026-10-01 创建，**最早 2026-10-15 才符合 14 天条款**（期间需保持 commits 活跃）。
- 提交方式：**不接受 PR**，走网页 issue 表单（"Click here to submit a new resource"），且**必须由人工提交**（明确写了不能用 `gh` CLI，不能是 bot）。
- 描述风格：陈述句、一行、无 emoji、不写销售话术。

---

## 二、Reddit 子版块规则评估（只看规则，未发帖）

### r/ClaudeAI（~730k–920k 成员）✅ 最适合，但有账号门槛

- 自我推广规则（多源交叉，2026-09）：项目必须是**用 Claude 做的 / 专为 Claude 做的**、免费可试、措辞克制 → 本 pack 完全符合（免费 MIT，为 Claude Code/agent skills 写的）。
- 有 "Built with Claude" showcase 惯例；affiliation 必须披露（明确说自己是作者）。
- ⚠️ **账号门槛**：feed 流帖子要求 50–100+ karma（不同来源口径不一），新号/低 karma 会被移到 megathread 或直接移除。vote manipulation（拉票）= 直接永封。
- 发帖形式：text post（self-post），讲清楚做了什么、怎么做的，链接放正文或首评论。
- 结论：内容契合度最高，但**需要一个有 karma 积累的 Reddit 账号**。若无现成账号，需先养号（正常参与讨论攒 karma）——这是当前最大卡点，需决策。

### r/AI_Agents（~333k 成员）⚠️ 只能走每周展示帖

- 规则：链接放评论不放正文；项目展示走 **weekly Project Display thread**；自我推广遵守 1/10 比例（10 个正常参与 : 1 个推广）。
- 结论：不适合独立发 Show 帖。动作 = 每周去 Project Display thread 留一条评论（披露作者身份 + 一句话介绍 + 链接）。

### r/ChatGPTPro（~614k 成员）⚠️ 次选，规则未直接核验

- 社区主题是"用 ChatGPT 及其他模型做事"，出现过带 disclosure 的 maker 自荐帖。
- 本 pack 是 Claude skills 格式（虽已是开放标准，Codex/Cursor/Gemini 也支持），契合度不如 r/ClaudeAI。
- reddit.com 本机被屏蔽，未能直接读取其 rules 页；**发帖前必须先读 live 规则**。

### 备选

- **r/ClaudeCode**（~310k）：更精准的目标用户（Claude Code 用户），规则与 r/ClaudeAI 同源，建议作为第二发帖点（不要同一天多版块发相同内容，会被判 spam）。
- **r/SideProject**（~800k）：明确允许自我推广，但极度反感广告腔，需用个人故事 + 失败教训口吻。

**通用红线**：同一内容不要一小时内 cross-post 多个版块；发帖后必须留守回评论，静默的 OP 会被当成 drive-by marketing。

---

## 三、Hacker News Show HN

官方指南（https://news.ycombinator.com/showhn.html，2026-10-01 已读）：

- Show HN 是给"别人能上手试的东西"：能在自己电脑上跑 / 拿在手里的。**Off-topic 明确包括：blog posts、sign-up pages、newsletters、lists**。
- ⚠️ **风险评估**：skill pack 处于边界——它不是链接列表（每个 SKILL.md 都是可直接丢进 `~/.claude/skills` 使用的），但形态上接近"合集"。建议正文**强调可试用性**（"copy one folder, restart Claude Code, it works"），弱化"列表"观感。
- 要求：non-trivial（"别发随手生成的 one-off"）→ 正文要讲清楚这 5 个 skill 的来历（从中文生产力包按英文职场语境重写，非机翻）。
- 标题必须以 `Show HN` 开头；发帖人必须在场参与讨论；**严禁拉票**（叫朋友 upvote 会被踩）。
- 时机（社区共识，非官方）：**美国工作日早上（太平洋时间 8–10am，即北京时间 23:00–次日 1:00）**曝光最好；避开周末和美国节假日。Show HN 只有一次首发机会，时间值得讲究。

---

## 四、物料草稿（英文，克制无 hype）

### PR 文案 1：ComposioHQ/awesome-claude-skills

**Title:** `Add English Productivity Skill Pack`

**Body:**

> This PR adds a link entry under **Productivity & Organization** for a free, MIT-licensed pack of 5 agent skills covering everyday knowledge-work tasks:
>
> - `tech-writing-proofread` — itemized proofreading checklist (typos, grammar, terminology consistency) that flags issues without rewriting the author's voice
> - `git-commit-message` — conventional-commit messages from staged diffs (imperative subject ≤50 chars + why-focused body)
> - `meeting-notes` — raw notes → structured minutes (conclusion first; every action item gets an owner and deadline)
> - `code-review-checklist` — five-axis review (correctness, security, readability, performance, test coverage), capped at 10 actionable comments
> - `deep-research-framework` — question definition → source tiering → cross-verification → conclusion-first reports with explicit uncertainty statements
>
> **Real-world use case:** these are the five tasks I kept re-explaining to my coding agent every week. Each skill encodes the workflow once so the agent follows it without repeated prompting. They were adapted (not machine-translated) from a Chinese-language productivity skill pack I use daily — examples, idioms, and conventions were rewritten for English workplace context.
>
> **Who it's for:** anyone using Claude Code / Claude.ai / API with skills enabled, doing docs, code review, or research reports.
>
> **Install:** copy `skills/<name>/` into `~/.claude/skills/` (or project `.claude/skills/`); no dependencies, no network calls, no sign-up.
>
> I reviewed and tested each skill manually before submitting this PR.

**Diff（README，Productivity & Organization，按字母序插入）：**

```markdown
- [Agent Skills — English Productivity Pack](https://github.com/alapha888/agent-skills-en) - Five free MIT skills for everyday knowledge work: proofreading docs, commit messages, meeting minutes, code review, deep-research reports. *By [@alapha888](https://github.com/alapha888)*
```

### PR 文案 2：sickn33/agentic-awesome-skills（5 个 skill 文件夹）

**Title:** `feat: add English productivity skill pack (5 skills)`

**Body:**

> Adds 5 community skills as `skills/<name>/SKILL.md` folders, adapted from https://github.com/alapha888/agent-skills-en (MIT, declared as `source_repo` in each frontmatter).
>
> | Skill | Category | What it does |
> |---|---|---|
> | tech-writing-proofread | writing | Itemized proofreading checklist; flags defects without rewriting voice |
> | git-commit-message | development | Conventional-commit messages from staged diffs |
> | meeting-notes | productivity | Raw notes → structured minutes with owned action items |
> | code-review-checklist | development | Five-axis review, max 10 actionable comments |
> | deep-research-framework | research | Source tiering + cross-verification + uncertainty statements |
>
> All five are `risk: safe` (text-only guidance, no shell/network/credential/mutation instructions). Validated locally with `npm run validate`. Source-only PR — no generated registry artifacts included.
>
> Background: adapted (not machine-translated) from a Chinese productivity skill pack used daily; examples and conventions rewritten for English workplace context. Manually reviewed each skill before submitting.

**Frontmatter 模板**（每个 SKILL.md 头部按此改写，保留正文）：

```yaml
---
name: <skill-name>
description: "<one-line description>"
category: <writing|development|productivity|research>
risk: safe
source: community
source_repo: alapha888/agent-skills-en
source_type: community
date_added: "2026-10-0X"
author: alapha888
tags: [<tag-one>, <tag-two>]
tools: [claude, cursor, gemini, codex]
---
```

### PR 文案 3：travisvn/awesome-claude-skills（⏳ 等 ≥10 stars 后用）

**Title:** `Add English productivity skill pack`

**Body:**

> Adds one entry under **Community Skills → Collections & Libraries**.
>
> https://github.com/alapha888/agent-skills-en — a free MIT pack of 5 English productivity skills for coding agents (proofreading, commit messages, meeting notes, code review, deep research). Each skill is a `SKILL.md` with frontmatter + workflow + minimal example + anti-patterns; adapted from a Chinese productivity pack I use daily, rewritten (not translated) for English workplace context. No dependencies, no sign-up.
>
> I wrote and adapted these skills myself, reviewed every file, and am submitting this PR manually.

**Diff（Collections & Libraries）：**

```markdown
- ** [agent-skills-en](https://github.com/alapha888/agent-skills-en) ** - Free MIT pack of 5 English productivity skills for coding agents: proofreading, commit messages, meeting notes, code review, deep research
```

（注：格式严格跟随该仓库 CONTRIBUTING 的 `- ** [Name](link) ** - 描述` 写法，注意空格。）

### Reddit 帖子草稿（r/ClaudeAI，text post）

**Title 选项：**
1. I kept re-explaining the same 5 workflows to Claude Code, so I turned them into skills
2. 5 free agent skills for the boring-but-weekly stuff: proofreading, commit messages, meeting notes, code review, research

**Body:**

> Disclosure: I'm the author. Free, MIT, no sign-up, no telemetry.
>
> I use Claude Code daily, and I noticed I was typing the same instructions every week: how I want docs proofread, how I want commit messages written, how meeting notes should turn into minutes, what a useful code review looks like, how research reports should handle uncertainty. So I encoded each one as an agent skill (`SKILL.md` + workflow + minimal example).
>
> What's in it (5 skills):
> - **tech-writing-proofread** — returns an itemized Original → Suggestion → Reason checklist; fixes language, never rewrites your voice
> - **git-commit-message** — conventional commits from staged diffs; subject ≤50 chars, body explains *why*
> - **meeting-notes** — conclusion first, then decisions / action items / open questions; every action item gets an owner and a deadline
> - **code-review-checklist** — five axes (correctness, security, readability, performance, tests), max 10 comments, no style nitpicks
> - **deep-research-framework** — define the question, tier sources, cross-verify, then write conclusion-first with explicit uncertainty statements
>
> These were adapted from a Chinese-language productivity pack I actually use — I rewrote the examples and conventions for English workplace context rather than translating. Happy to be told where the workflows are wrong; that's the fastest way to improve them.
>
> Install: copy `skills/<name>/` to `~/.claude/skills/`, restart session. Repo: https://github.com/alapha888/agent-skills-en

**发帖前检查：** Built with Claude flair（如有）；账号 karma ≥50；链接放正文（该版块允许 feed 帖带项目链接，referral 链接除外）；发帖后 24h 内回复所有评论。

### Show HN 草稿

**Title:** `Show HN: 5 free agent skills for everyday knowledge work`

**Body（随帖正文 / 首评论）：**

> I kept giving my coding agent the same instructions every week — how to proofread a doc without rewriting my voice, how to write a commit message, how to turn meeting notes into minutes, what makes a code review useful, how to structure a research report. I finally encoded each workflow as an agent skill.
>
> It's 5 markdown files (SKILL.md + workflow + minimal example + anti-patterns), MIT licensed, no dependencies:
> - tech-writing-proofread, git-commit-message, meeting-notes, code-review-checklist, deep-research-framework
>
> They started as a Chinese-language productivity pack I use daily; I adapted (not translated) them for English workplace context — the proofreading skill, for example, covers dangling modifiers and Oxford comma consistency instead of Chinese-specific punctuation rules.
>
> Try it: copy any `skills/<name>/` folder into `~/.claude/skills/` and ask Claude to do the corresponding task. Works with any agent host that supports the skills format.
>
> https://github.com/alapha888/agent-skills-en
>
> I'm around for questions and for being told where the workflows are wrong.

---

## 五、建议执行顺序 + 待决策

| 顺序 | 动作 | 状态 |
|---|---|---|
| 1 | ComposioHQ PR（文案就绪） | 可立即执行 |
| 2 | agentic-awesome-skills PR（需先做 5 个文件夹的 frontmatter 改写 + 本地 validate） | 需半天准备 |
| 3 | Show HN（选一个美西工作日早晨，即北京时间深夜） | 择时一次 |
| 4 | r/ClaudeAI 发帖 | ⚠️ 卡点：需要有 karma 的 Reddit 账号；无则先养号 |
| 5 | r/AI_Agents 每周 Project Display thread 评论 | 低优先级顺手做 |
| 6 | travisvn PR | 等仓库 ≥10 stars |
| 7 | hesreallyhim issue 表单（人工网页提交） | 等 2026-10-15（14 天条款） |

**需复核/决策的事项：**
1. travisvn 与 hesreallyhim 都有"禁止 AI 提交"条款 → 建议 PR/表单由阿发本人点提交，或至少人工署名。由谁点提交需定。
2. Reddit 账号：有无现成带 karma 的号？无则列入养号计划（不自行注册新号刷 karma）。
3. Show HN 的"lists are off-topic"边界风险已在文案中用"可试用性"对冲，是否接受该风险需复核。
4. agentic-awesome-skills 的 PR 需要把 5 个 SKILL.md 按对方 frontmatter 改写一遍（约半天工作量），是否值得做需复核——它是 47k stars 的一键安装生态，值得，但工作量最大。
