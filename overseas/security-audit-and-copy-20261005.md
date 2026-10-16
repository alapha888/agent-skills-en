# Skills 安全自查 + 信任文案包（2026-10-05，待主 agent 选用，未发布）

## 为什么现在做

Feed 2026-10-04 的一条（Claude Code Mods 复盘，dev.to）引用了一项覆盖 31,132 个 agent skills 的研究：26.1% 至少带一个安全漏洞（数据外泄 13.3%、权限提升 11.8%），且**捆绑可执行脚本的 skill 出漏洞概率是指令型（instruction-only）的 2.12 倍**。原文已实读核验：
https://dev.to/max_quimby/claude-code-mods-just-turned-agents-into-a-platform-5gc0 （正文 "The skills gold rush..." 段）

自家在售/在分发的两个技能包恰好全是 instruction-only，这是现成的信任卖点，但 README 和所有已发文章里从没提过。本包把自查做完、文案写好，选用即可发。

## 自查结果（2026-10-05 本地实测，只读）

范围：`agent-skills-en/skills/`（5 个）+ `agent-skills-zh/skills/`（5 个）

- 文件构成：两个仓库除 LICENSE 与截图 png 外**只有 .md**；每个 skill 就是单个 `SKILL.md`，无 scripts/、无二进制、无依赖清单。
- 体量：EN 五个合计 283 行，ZH 五个合计 277 行——用户装之前可以全文读完。
- 风险模式扫描（curl / wget / sudo / rm -rf / api key / token / credential / 上传外发 / 忽略上文指令 等关键词）：**0 命中危险项**。仅有的相关命中是正面的：`git-commit-message` 示例里的 `git commit` 命令、`code-review-checklist` 本身就是教人查「密钥硬编码/SQL 与命令拼接」的。
- 结论（口径克制版）：本包不执行任何代码、不访问凭据、不联网、不外发数据；风险面只剩「指令本身写了什么」，而指令全文公开可审。

## 文案 1：README 安全段（EN，贴在 Install 段之前即可）

## Security: nothing to execute

A study of 31,132 published agent skills found 26.1% contained at least one security vulnerability — and skills that bundle executable scripts were 2.12× more likely to be vulnerable than instruction-only ones ([coverage](https://dev.to/max_quimby/claude-code-mods-just-turned-agents-into-a-platform-5gc0)).

This pack is instruction-only by design:

- Each skill is a single `SKILL.md` — plain Markdown, no scripts, no binaries, no dependencies.
- All five skills together are 283 lines. You can read every word before you install.
- No skill touches credentials, the network, or your files on its own; it only tells your agent how to structure a task.

## 文案 2：短帖草稿（dev.to 第 7 篇候选 / Hashnode 备用，约 350 词）

Title: **26% of agent skills have a security hole. Mine ship zero lines of code.**

Tags: `ai`, `security`, `productivity`

A study making the rounds this week analyzed 31,132 agent skills and found 26.1% contained at least one security vulnerability — data exfiltration in 13.3% of cases, privilege escalation in 11.8%. One detail in it matters more than the headline: skills bundling executable scripts were 2.12× more likely to carry a vulnerability than instruction-only packages.

That is a design choice, not luck. When I built my five-skill pack (commit messages, code review, meeting minutes, tech-writing proofreading, deep-research framing), I kept every skill to a single SKILL.md file:

- No scripts, no binaries, no dependencies — nothing runs.
- 283 lines total across all five files. The full audit surface fits on a few screens, and "installing" means reading them.
- The only shell command anywhere in the pack is an example `git commit` inside the commit-message skill's sample output.

Instruction-only skills can't do everything — they won't fetch an API or transform a binary. But for knowledge-work structure (how a review should be organized, what a good research report must cite), execution is not the point. The workflow is.

If you install third-party skills, the cheapest security review is a file listing: `find . -type f`. If you see code you didn't expect, read it before your agent does. And if a skill is longer than you would ever read, that is the risk — not a footnote to it.

The pack (MIT, free): https://github.com/alapha888/agent-skills-en

## 使用说明

- 文案 1 贴入 README 属于对外发布动作，按既有授权由主 agent / 自主循环执行，本文件只备稿不落 README。
- 数字口径：26.1% / 13.3% / 11.8% / 2.12× 均出自上面 dev.to 复盘文引用的研究；发稿时保留「a study of 31,132 skills」归因句，不要改成自家实测口径。
- ZH 包同为零代码，爱发电商品页如需中文版信任句可直译文案 1，无需另查。
