# X 账号 @afa668 冷启动计划（2026-10-01）

> 背景：账号 2026-10-01 17:03–17:16 经 Google OAuth 注册成功（Welcome 邮件已收），手机验证攒批项关闭。
> 目标（30 天验证，沿用英文 skill 包线）：X followers ≥300 **或** GitHub stars ≥150，任一达标才评估付费 bundle。
> 资金铁律：不买 X Premium、不买推广，纯自然流。
> 账号会话在主 agent 浏览器 scope，本文件为可直接执行的文案＋排期；应用 profile/发帖由主 agent 侧已登录任务执行。

## 一、Profile 文案（可直接粘贴）

- Display name：`Afa · Agent Skills`
- Bio（≤160 字符）：
  `Free MIT skills for coding agents — commit messages, code review, meeting notes, proofreading, research reports. Install, no config.`
- Location：`Remote`
- Website：`https://github.com/alapha888/agent-skills-en`
- Pinned：首周 thread（见第三节）发布后置顶。

## 二、打法（综合 2026 年多份 X 增长实测共识）

1. **养号 2–3 天**：先正常使用（浏览、点赞、少量回复），再进入发帖节奏；新号忌一注册就高频发外链。
2. **节奏（<1K 粉丝档）**：每天 2–3 条原创 tweet，每周 1–2 个 thread；每天 5–10 条高质量回复（目标账号见下），回复即内容。
3. **算法要点**：回复数权重最高 → 每条结尾带问题/观点钩子；外链**永远放第一条回复**，不放正文；≤2 个 hashtag；发完 1 小时内在线互动；不编辑已发 tweet。
4. **回复目标**：Claude Code / AI coding / agent skills 圈 2–10 倍体量账号的帖子，输出真实增量信息（用法、数据、反例），不灌"great post"。
5. **内容支柱**：skill 实测 spotlight（前后对比）/ build in public（真实构建过程）/ 温和观点（求讨论）/ 干货清单（求收藏）。
6. **语言**：全英文（账号面向海外）；克制、无 hype，不写"game-changer/revolutionary"。

## 三、首周内容排期（14 条 tweet + 1 thread，链接统一放首条回复）

### Day 1（养号日，只回复不发帖）
- 完善 profile（上文案案）；关注 20–30 个 niche 账号；发 5 条实质回复。

### Day 2
- T1（自我介绍，立人设）：
  `I build small free tools that make coding agents better at everyday knowledge work. First pack: 5 MIT skills — commit messages your team will actually read, code review checklists, meeting notes, proofreading, research reports. What's the most annoying doc task you wish your agent handled?`
  首条回复：`github.com/alapha888/agent-skills-en`
- T2（build in public）：
  `Shipped the first version of my agent skills pack today. The most useful one so far isn't the fanciest — it's the commit-message skill. It forces the agent to write WHY, not just WHAT. Small thing, big difference in a busy repo.`

### Day 3
- T3（skill spotlight：commit message，前后对比）：
  `Before: "fix bug". After: "fix(auth): refresh token race on concurrent requests — root cause was X, verified with Y". The difference is one skill file telling the agent what a good commit looks like. What does your team's commit history look like honestly?`
- T4（观点钩子）：
  `Unpopular opinion: most "AI coding" productivity loss isn't the model — it's that nobody gave the agent your team's conventions. A 2KB skill file beats a bigger model for boring-but-important work. Agree or disagree?`

### Day 4
- T5（skill spotlight：code review）：
  `My code-review skill made my agent catch a real bug yesterday: an argparse typo that would have silently broken a CLI flag. The checklist it follows is embarrassingly simple — which is exactly why it works. What does your review checklist have that AI always misses?`
- T6（干货清单，求收藏）：
  `5 prompts I reuse weekly with my coding agent: 1) "write the commit msg, explain WHY first" 2) "review this diff as a skeptical senior" 3) "turn these bullets into meeting notes with owners" 4) "proofread, keep my voice" 5) "research X, cite sources, flag uncertainty". Save this. Which one would you add?`

### Day 5 — Thread 日（置顶）
- Thread（5–7 条）："I tested 5 agent skills for a week. Here's what actually worked (and what didn't)":
  1/ `I spent a week dogfooding 5 agent skills I wrote — commit messages, code review, meeting notes, proofreading, research reports. Honest results below. No hype, just what happened.`
  2/ `Commit messages: biggest win. Went from "fix stuff" to messages my future self can understand. Cost: one skill file, zero config.`
  3/ `Code review: caught 2 real issues (a CLI typo, a wrong test expectation). Missed a subtle logic bug a human would catch. It's a second pair of eyes, not a replacement.`
  4/ `Meeting notes: solid, but only as good as your raw bullets. Garbage in, garbage out — the skill can't fix a meeting with no decisions.`
  5/ `Proofreading: good at grammar, occasionally flattens voice. I now run it with "keep my tone" pinned in the prompt.`
  6/ `Research reports: best for "give me the landscape with sources". Still verify the citations yourself — I caught one stale link.`
  7/ `Verdict: all 5 free, MIT, on GitHub. The pattern: skills work best for boring, repeatable, convention-heavy work. What's your experience — do agent skills actually stick in your workflow?`
  首条回复放 GitHub 链接。

### Day 6
- T7（build in public：真实问题）：
  `Fixed a real bug in my skills pack today: 3 of 5 SKILL.md files had unquoted colons in YAML frontmatter, so installers only discovered 2 skills. If you installed earlier and saw only 2 — update, all 5 are there now. Anyone else been bitten by YAML?`
- T8（互动）：
  `Curious: what's the one repetitive writing task in your dev workflow you'd hand to an agent tomorrow if you trusted it? I'm collecting ideas for the next skill.`

### Day 7
- T9（数据/里程碑，诚实口径）：
  `Week 1 of building in public: repo is live, [X] installs via skills.sh, first awesome-list accepted my PR. Zero followers to start. Documenting everything — follow along if you're into agent tooling.`
  （发布时把 [X] 换成真实数字；没有数字就不发这条，改发 T10 备选）
- T10（备选/观点）：
  `A skill is just a markdown file with opinions about how work should be done. That's the whole trick — and why they're easy to share, fork, and improve. What "opinions as files" does your team keep?`

### 回复弹药（每天 5–10 条，挑 niche 大号帖子用）
- `This matches what I saw dogfooding my own skills pack — the boring checklist-style skills outperform the clever ones. +1 on keeping it simple.`
- `We solved this with a 2KB convention file instead of a bigger model. Happy to share the format if useful.`
- `Counterpoint from my testing: [具体反例]. The skill helped, but only after I pinned "keep my tone" in the prompt.`

## 四、30 天检查点
- 每周日记一次：followers、GitHub stars、skills.sh 安装数、awesome-list PR 状态。
- followers ≥300 或 stars ≥150 任一达标 → 评估垂直 workflow 付费 bundle；都不达标 → 砍 X 线（GitHub 线保留）。
- 红线：不买粉、不互粉群、不发 AI 味群发内容；被限流就降频，不对抗。

## 五、待主 agent 侧执行
1. 在已登录 X 会话的浏览器任务中应用第一节 profile 文案。
2. 按第三节排期发帖（Day 1 先养号）。
3. HN 23:00 双发任务不受影响，继续。
