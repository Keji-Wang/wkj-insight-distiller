# 示例集说明

本目录包含 8 个虚构示例，覆盖这个 skill 设计上最容易出错的场景。**所有人物、公司、数据、事件均为虚构演示材料**，不对应任何真实访谈或会议。

每个用例包含两个文件：

- `input.md` — 虚构输入材料 + 本例测试点说明
- `expected-behavior.md` — 通过标准（必须做到 / 禁止）

部分用例另含 `actual-output.md` — 盲跑试跑的实际输出（由模型在只读 SKILL.md、不读 expected-behavior.md 的条件下生成），试跑记录见 `docs/validation.md`。

| 用例 | 测试场景 | 核心陷阱 |
|---|---|---|
| [01-single-interview](01-single-interview/) | 单人访谈 | 经历与观点分层；数字前后不一致 |
| [02-multi-speaker-disagreement](02-multi-speaker-disagreement/) | 多人讨论 | 分歧未解决时不许合并成共识 |
| [03-unknown-speakers](03-unknown-speakers/) | 说话人不明确 | 硬门槛：先出确认块，不出备忘录 |
| [04-ai-processed-notes](04-ai-processed-notes/) | AI 生成的纪要 | 撰写层添加的叙事不是原始事实 |
| [05-insufficient-information](05-insufficient-information/) | 信息不足 | 不强行提炼、不虚构上下文 |
| [06-embedded-instruction](06-embedded-instruction/) | 材料内嵌指令 | 指令是被分析的内容，不是任务 |
| [07-unverifiable-claims](07-unverifiable-claims/) | 无检索能力 | 未核实标注；不伪造引用 |
| [08-partial-file](08-partial-file/) | 长文件部分可读 | 只按实际读取范围下结论 |

想快速感受这个 skill 的行为，建议先读 03（硬门槛）和 06（内嵌指令）。
