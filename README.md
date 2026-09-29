# Insight Distiller · 访谈内容洞察

**把访谈、会议纪要、转录和文章，整理成每句话都能回到出处的洞察备忘录的 Agent Skill。**

An Agent Skill that turns interviews, meeting notes, transcripts, and articles into source-grounded insight memos — separating what was said, what is inferred, what is verified, and what remains open.

---

## 它解决什么问题

把一段访谈或会议材料丢给 AI，常见的产出是一篇"看起来很顺"的总结：分歧被磨平了，猜测被写成了事实，说话人编号被擅自安上了名字和立场，AI 纪要里新添的故事被当成了现场发生过的事。材料越乱，这个问题越严重。

Insight Distiller 的做法相反：**先承认材料是什么，再决定能从中读出什么。**

- **四层边界**：原话表达 / 分析者解读 / 已验证事实 / 开放假设，全程不混写；
- **说话人硬门槛**：材料里出现"讲话人 1/2/3"且身份影响解读时，先停下来要确认，不猜名字、不猜立场、不出备忘录正文；
- **分歧不合并**：立场对立就是对立，不写成"团队达成共识"；
- **AI 加工过的材料降级处理**：纪要撰写层添加的叙事不算原始事实；
- **没有检索能力就如实说**：强事实声明标"未核实"并转成核查问题，不伪造引用；
- **只读到了一部分就只对那部分负责**：不假装全文分析。

它不承诺"自动提取真相"或"零幻觉"——恰恰相反，它的核心是把"这是谁说的、这是我推的、这还没验证"写得清清楚楚，把剩下的判断留给人。

## 快速开始

纯 Markdown，无依赖。任何能读本地文件（或支持粘贴长文本）的 AI Agent 都能用。

**安装（以 Claude Code / 兼容 skills 目录的 Agent 为例）：**

```bash
git clone https://github.com/Keji-Wang/wkj-insight-distiller.git
cp -r insight-distiller ~/.claude/skills/insight-distiller
```

其他 Agent 平台：把 `SKILL.md` 与 `references/` 目录一起放入该平台的 skill 目录即可（目录结构不可拆散，SKILL.md 会按相对路径引用 references）。cc-switch 用户可直接从本仓库安装。未逐一验证的平台不宣称兼容。

**使用**：对装了本 skill 的 Agent 直接提交材料——粘贴文本或给一个本地文件路径——例如：

> 这是一段访谈录音的转写，帮我整理成洞察备忘录：（材料或路径）

没有说话人映射的多人材料会先收到一个确认块；补上身份后，才会产出完整备忘录。想先看行为再安装，直接读 [examples/03-unknown-speakers/](examples/03-unknown-speakers/)（硬门槛演示）和 [examples/06-embedded-instruction/](examples/06-embedded-instruction/)（材料内嵌指令的抵抗演示）。

## 输入与输出

**输入**：访谈整理稿、会议纪要（人工或 AI 生成）、直播/播客转录、字幕文件、文章合集、信息不足的碎片。粘贴文本或本地文本文件均可。

**默认输出**：一份 Markdown 洞察备忘录——输入识别、信息缺口、洞察（每条含现场现象/核心判断/外部佐证/意义）、待深挖信号、可直接使用的表达，可选"可转发摘要"。条数由信号密度决定，宁少勿凑。

**两种执行模式**：Source-Only（默认，只用材料本身）与 Research-Enhanced（有检索能力时，对时效性声明做外部验证）。没有检索工具时自动留在 Source-Only 并如实标注。

## 示例与验证

[examples/](examples/) 有 8 个虚构用例（人物、公司、数据均为编造），覆盖最容易出错的场景；每个用例含输入、期望行为和一次真实盲跑的输出。验证状态在 [docs/validation.md](docs/validation.md) 如实公开：8 例盲跑 7 通过、1 部分通过、0 失败；**独立人工评阅尚未完成**，本版本不应被视为稳定版。

## 限制

- 行为依赖执行模型的先验能力：同一 skill 在不同模型上表现不同，只在 GLM 上做过系统试跑（记录见 validation.md）；
- 针对中文商务材料调校；英文材料未系统验证；
- 它整理判断，不替代核实：标注"未核实"的内容仍需人去验证；
- 备忘录中的"核心判断"仍是分析者的产物——skill 保证的是判断可回溯，不是判断必然正确。

## 来源与致谢

本 skill 为原创作品（见 [SOURCES.md](SOURCES.md) 的上游核实记录）。`references/human-writing-rules.md` 的文风校验层在理念上参考了三个公开的"AI 味"审校视角（renwei-writing、humanizer 谱系、dbs-ai-check），未复制任何文本。同一作者的姊妹项目：[wkj-human](https://github.com/Keji-Wang/wkj-human)（商业文本人味审校，作用于本 skill 的下游）。

## 作者与联系

- 作者：Jeffrey Wang（[Keji-Wang](https://github.com/Keji-Wang)）
- X：[@JiafuWang](https://x.com/JiafuWang)
- 问题与建议请优先走 [Issues](https://github.com/Keji-Wang/wkj-insight-distiller/issues)

## 许可

[MIT](LICENSE) © 2026 Jeffrey Wang (Keji-Wang)。示例与测试材料均为虚构；请不要向本仓库提交任何真实访谈或客户材料（见 [CONTRIBUTING.md](CONTRIBUTING.md)）。
