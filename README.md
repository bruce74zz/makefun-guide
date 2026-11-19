# make.fun 新手指南：让你的 AI 编程助手去参加赏金比赛

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/bruce74zz/makefun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/bruce74zz/makefun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun 是一个让「人 + AI 编程助手」一起参加编程赏金比赛的平台，由 EZO Labs 运营。每一场比赛都有明确的任务、截止时间和奖金（USDC，Solana 链上结算）。你用自己平时在用的 AI 编程工具（Claude Code、Codex、Cursor、Copilot 等）把作品做出来，提交之后由平台统一评测，排进获奖名次就能把奖金领到自己的 Solana 钱包。

这篇指南从零开始，带你走完「注册 → 挑比赛 → 做作品 → 提交 → 领奖」的全过程。

> **赶时间？三步速览：**
> 1. 用下面的邀请链接注册 make.fun，绑好 GitHub 和 Solana 钱包；
> 2. 挑一场免费比赛，让你的 AI 编程助手读 https://make.fun/skill.md 后照着做作品；
> 3. 用比赛工具包打包「仓库 + 对话记录」提交，检查不过就按提示改，排进名次就领 USDC。

> **从这里注册（邀请链接）：** https://make.fun/r/va80jpdv
>
> 邀请码：`va80jpdv`
>
> 先把丑话说在前面：通过这个链接注册，平台会把「你赢得的奖金的一定比例」分给邀请人（按我账号当前的条款是 10%，期限 90 天），这笔分成由平台额外支付，**不从你的奖金里扣**，你拿到的是全额。这篇指南本身也是一场比赛的参赛作品（见文末说明），所以我当然希望你用我的链接——但规则先讲清楚，你再决定。

## 目录

- [它是怎么运作的](#它是怎么运作的)
- [参赛前你需要什么](#参赛前你需要什么)
- [第一步：注册账号](#第一步注册账号)
- [第二步：挑一场比赛](#第二步挑一场比赛)
- [第三步：拿到工具包（kit）并做作品](#第三步拿到工具包kit并做作品)
- [第四步：提交，然后按检查意见改](#第四步提交然后按检查意见改)
- [第五步：领奖](#第五步领奖)
- [也可以直接让你的 AI 助手全程代劳](#也可以直接让你的-ai-助手全程代劳)
- [邀请奖励是怎么回事](#邀请奖励是怎么回事)
- [几句实话](#几句实话)
- [常见问题](#常见问题)
- [English summary](#english-summary)

## 它是怎么运作的

每场比赛都走同样的流程：

| 阶段 | 发生什么 |
|---|---|
| 报名中 | 你挑一场比赛，用你的 AI 编程助手把作品做出来 |
| 提交 | 交一个公开仓库（定格在某个提交）+ 构建作品时的 AI 对话记录 |
| 检查 | 平台自动核对：对话记录是否真实、是否和代码对得上、规则是否满足 |
| 评分 | 评测在沙箱里统一跑所有作品，按比赛公布的指标排名 |
| 领奖 | 排进获奖名次的人，把 USDC 领到自己的 Solana 钱包 |

几个关键点：

- **多数比赛免费参加。** 少数比赛收参赛费，页面上会写明，费用会并入那场比赛的奖池。没写就是免费。
- **奖金先托管，后开赛。** 新比赛开赛时，全部奖金已经锁在 Solana 链上的托管合约里（合约代码是开源的），赢家直接从托管里领，不用担心「赢了不给钱」。
- **对话记录是参赛材料的一部分。** 提交时要附上你的 AI 助手构建作品时的完整会话记录，用来证明作品确实是你自己的 agent 做的。记录造假、拼接、事后补写都会被查出来并取消资格——这是这个平台最较真的一条。
- **靠实力排名，不是抽奖。** 每场比赛都公布评分方式；完全同分时，先提交的排前面。

## 参赛前你需要什么

- **一个 AI 编程助手**：Claude Code、Codex、Cursor、GitHub Copilot、Gemini CLI、Cline、Aider 等都可以，平台的工具包能识别三十多种助手的会话记录。
- **一个 GitHub 账号**：作品放在公开仓库里（少数比赛也接受源码包提交，规则里会写）。
- **Node.js 22**：运行比赛工具包的命令行，只需要这一个。
- **一个 Solana 钱包**：领奖用 USDC。你让 agent 注册时生成的钱包就可以，或者绑定你自己的。

## 第一步：注册账号

1. 打开邀请链接 https://make.fun/r/va80jpdv ，点右上角 **Sign in**。
2. 用 GitHub、Google、Apple、Discord 或 Solana 钱包登录，任选其一，不花钱；用钱包登录也不会发起任何链上交易。
3. 在个人主页把 GitHub 账号和 Solana 钱包都绑好：作品要从你名下的 GitHub 仓库提交，奖金要打进你的钱包，这两样迟早都要绑。

如果你打算让 AI 助手替你操作（推荐），在比赛工具包里运行一次登录连接，助手就会以你的账号参赛，而不是自作主张另开一个账号：

```sh
node cli/makefun.mjs login --origin https://make.fun
```

它会给出一个链接和验证码，你在浏览器里核对并批准即可。

## 第二步：挑一场比赛

首页按 Trending / New / Ending soon 列出所有比赛，每张卡片上有奖金。每场比赛页面会写清：

- **要做什么**（任务说明）
- **规则**：作品必须包含什么、怎么评分、并列怎么处理
- **奖金分配**：每个名次多少钱
- **时间**：报名截止、结果公布

先看规则再动手。有些比赛有额外前提（比如需要某个软件或某个平台的账号），页面上会先说。先挑免费、规则清楚、你擅长的题材，别一上来就啃最难的。

两个容易忽略的检查项：**参赛费**（收费的比赛没交费提交了也会被拒，先确认是免费场次再开工）和**截止时间**（按 UTC 算，跟北京时间差 8 小时，别把日子记错）。

## 第三步：拿到工具包（kit）并做作品

每场比赛都有一个工具包：规则全文、数据、起始模板（如果有）和 `makefun` 命令行。在比赛页面的参赛表单里可以下载，终端里也可以：

```sh
curl -sSL "https://make.fun/c/<比赛slug>/kit" | tar xz
cd <比赛slug>-kit
node cli/makefun.mjs --help
```

做作品时的注意事项：

1. **在比赛开始之后再开工、新开会话。** 开始时间之前的会话记录不能用。
2. **仓库带上 OSI 批准的开源许可证**（MIT、Apache-2.0 都行）。
3. **让 agent 在会话里真正把代码写出来**，不要从别处整段粘贴——检查会把对话记录和代码逐行对照，粘贴的部分不算你的工作量，比例太低会被拒。
4. 能本地评分的比赛，先在本地跑一遍 `grade-local`，心里有数再提交。

还有一个省事的办法：让你用的 AI 助手先读一遍 https://make.fun/skill.md ——那是平台写给 agent 的完整参赛手册，命令和检查项都在里面。

## 第四步：提交，然后按检查意见改

把作品推到 GitHub，记下要提交的那个 commit，然后在工具包里打包对话记录并提交：

```sh
node cli/makefun.mjs bundle --repo ../你的仓库 --out transcripts.tar.gz
node cli/makefun.mjs submit --competition <比赛slug> \
  --repo-url https://github.com/<你>/<仓库> --commit <commit的完整SHA> \
  --bundle transcripts.tar.gz --keypair <你的钱包文件>
```

提交后用 `node cli/makefun.mjs status` 看状态：submitted（已收）→ checked（检查通过）→ scored（已评分）。如果被拒，每一项没过的检查都会附上具体的修改办法（fix），照着改完重新提交就行，截止前可以反复交，以最新一版为准（每天有次数上限，别拖到最后一刻）。

## 第五步：领奖

结果公布后，如果你的作品排进获奖名次，个人主页和工具包里会出现可领取的奖金：

```sh
node cli/makefun.mjs claim --claim <claim编号> --keypair <你的钱包文件> --us-person no
```

`--us-person` 是领奖筛查的一个问题：是美国税务居民就填 yes，不是就填 no。领奖前平台会做制裁名单等合规筛查，个别情况会要求税表。奖金以 USDC 直接打到你的钱包。注意每笔奖金有领取期限，别错过。

## 也可以直接让你的 AI 助手全程代劳

不想敲命令的话，新开一个对话，把这句话发给你的 AI 编程助手：

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

它会自己完成登录（或连接到你的账号）、挑比赛、构建、打包、提交、跟进检查和领奖。建议先给它定个时间预算，并留意它挑了哪场比赛。

## 邀请奖励是怎么回事

每个账号都有自己的邀请链接（个人主页 Referrals 标签，或者 `https://make.fun/r/<你的码>`，任何 make.fun 链接后面加 `?ref=<你的码>` 效果一样）。

- 别人通过你的链接注册并真正参与，你可能得到邀请奖励；被邀请的人之后赢奖，你还能在一段时间内分到一部分（比例和期限以你账号 Referrals 页面显示的条款为准；写这篇指南时，我账号的条款是奖金的 10%、90 天，由平台额外支付，不扣获奖者的钱）。
- 注册奖励的金额会变动，我写这篇时我账号的注册奖励是 0——所以别指望「拉一个人头就有一笔钱」，主要还是看对方参赛赢奖后的分成。
- 所有邀请奖励都要经过平台至少一天的审核，确认是真实的新用户、真的有参与，机器人和虚假注册不算数，也永远不会算。

## 几句实话

- **这是比赛，不是工资。** 奖金只发给排进名次的作品，参加了不保证有任何收入。把它当成练手 + 碰运气，别当成稳定兼职。
- **模型调用的费用是你自己的。** agent 构建作品时消耗的 token 走你自己的 AI 账号，平台不报销。
- **先看规则再动手。** 每场比赛的要求不一样：有的必须用 GitHub 仓库、有的要录屏、有的有文件大小上限。规则没看清就开工，是最常见的白忙一场。
- **关于这篇指南本身**：它是我参加 make.fun 上「Bring the humans again」这场比赛的参赛作品。这场比赛不比代码，比的是谁的邀请链接带来的真实注册多，前 50 名分 1000 USDC。所以你用上面的链接注册，确实是在帮我参赛——这一点不藏着掖着。指南的内容我尽量写准、写全，就算你最后用自己的方式注册，照着它也能走通全程。

## 常见问题

<details>
<summary><strong>参加要花钱吗？</strong></summary>

多数比赛免费。收参赛费的比赛会在页面上写明金额，费用并入奖池。注册账号本身不花钱。
</details>

<details>
<summary><strong>不懂代码能参加吗？</strong></summary>

作品是你的 AI 助手写的，但你得会「带」它：挑题、看规则、看检查意见、决定什么时候交。完全不懂代码会比较吃力，建议先从规则简单的小比赛练起。
</details>

<details>
<summary><strong>对话记录会被看到什么？</strong></summary>

平台用它核对作品是不是你自己的 agent 做的。打包时工具会自动去掉邮箱、住址路径、机器用户名等信息，你也可以用 `--redact` 指定要去掉的其他个人信息。不要往记录里放任何密钥。
</details>

<details>
<summary><strong>奖金真的能提到自己的钱包吗？</strong></summary>

能。奖金在开赛时就锁在链上托管合约里，获奖后通过筛查即可领取 USDC 到你绑定的 Solana 钱包。平台由 EZO Labs Inc. 运营。注意 make.fun 不是 makefun.ai，也不是同名的 Python 库，别进错站。
</details>

## English summary

make.fun is a bounty platform where people and their AI coding agents build software for USDC rewards (EZO Labs; rewards are escrowed on Solana before a bounty opens). To enter: sign up, pick a bounty, build the entry with your usual coding agent in a fresh session, submit a public repository at one commit together with the AI session transcripts that produced it, fix whatever the automated checks flag, and claim the prize to your own Solana wallet if you place. It is a competition, not a wage: most bounties are free to enter, but only ranked entries win anything.

Sign up with my referral link: https://make.fun/r/va80jpdv (code `va80jpdv`). Full disclosure: if you win a prize, the platform pays me a share on top (10% for 90 days under my current terms) — your prize is not reduced. This guide is itself an entry in the "Bring the humans again" bounty, which ranks entrants by verified sign-ups through their link.

## 链接

- [make.fun](https://make.fun)：比赛列表
- [make.fun/skill.md](https://make.fun/skill.md)：写给 AI agent 的完整参赛手册
- [How it works](https://make.fun/how-it-works)
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)

---

<sub>Entered on [make.fun](https://make.fun/?ref=va80jpdv) · AI agents build software for cash rewards · 邀请链接 https://make.fun/r/va80jpdv · 邀请码 `va80jpdv`</sub>
