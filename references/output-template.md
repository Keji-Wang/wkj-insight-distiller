# Output Template

Use this as the default memo structure.
Adapt lightly when the source type requires it, but keep the judgment chain readable.

## Pre-memo gate

Before using any memo structure below, check whether numbered speakers are still unconfirmed.

If yes, do not start the memo yet.
Output only this confirmation block:

```markdown
## 待确认信息
- 讲话人1：
  - 识别提示：
  - 请确认：这位是谁？属于哪一方？

- 讲话人2：
  - 识别提示：
  - 请确认：这位是谁？属于哪一方？
```

Only after confirmation should you use the memo templates below.

## Preferred final memo

Use this when delivering a polished internal insight note.
Let the memo read from judgment to evidence, not from checklist to checklist.
Write under the constraints in [human-writing-rules.md](human-writing-rules.md).

Important for interview or meeting material:

- do not blur `speaker said` and `I infer`
- if a sharp line is your synthesis, make sure the surrounding paragraph shows it is interpretation rather than verbatim source claim
- if role, authority, or endorsement level matters, make that context visible early

```markdown
# [标题]

## 输入识别
- 输入类型：
- 材料层级：
- 执行模式：Source-Only / Research-Enhanced
- 交互画像：local-interactive / workflow-confirmed / form-constrained / portable-open
- 讲话人映射：
- 对话场景：

## 信息缺口
- 若无明显缺口，可写“本轮无关键缺口”
- 若有关键缺口，明确写出哪些判断因此只能视为暂定

## 这份材料里真正值得提炼的，不只是……
[用 1-3 段先把这份材料为什么值得看讲清楚。不要一上来就拔高，也不要急着写漂亮话。]

## 洞察（条数由信号密度决定，宁少勿凑）

[条数不固定：2-5 条均可；若材料只支撑 1 条强判断，就只写 1 条。不要为了填满格子而凑数——"洞察一/二/三"式的固定三段正是 SKILL.md 明确禁止的排比陷阱，会诱导把弱观察包装成洞察。每条保留下面的四层结构，按内容强度排序，不套固定编号。]

### 洞察：[一句话判断]

#### 现场现象
- [按需列举，不强制条数]

#### 核心判断
[不要重复现象，要给出更高一层的解释。优先用朴素、直接、能落地的句子。]

#### 外部佐证
- [已验证事实 / 高可信背景，按需列举；Source-Only 模式若无外部验证，写明"本轮未做外部验证"，不要编造]

#### 这条洞察的意义
[解释为什么这条判断值得进入知识库、客户沟通或长期观察。]

[按下一条信号强度决定是否继续。没有下一条硬信号就停，不要补弱项凑数。]

## 最值得继续深挖的信号

### 1. [问题]
[为什么值得继续追]

### 2. [问题]
[为什么值得继续追]

## 可直接使用的表达
- [按需列举，宁少勿凑；只收真正可复用的硬表达，不为凑数扩列]

## 还需要补充的信息
- 待补充项 1
- 待补充项 2

## 参考来源
- 来源 1
- 来源 2
```

## Optional forwardable version

If the result may be forwarded to leaders, partners, or external-facing internal stakeholders, add a shorter second layer:

```markdown
## 可转发摘要
[用 3-6 句话写成一版适合转发的短摘要。]

## 可直接转发的判断
- [2-4 条，按转发价值排序；不强制三条，宁少勿凑]
```

Rules:

- no recording-process wording
- no "AI summary may be inaccurate"
- no debugging or method explanation
- no overconfident line that cannot survive being forwarded

## Working memo / analysis worksheet

```markdown
# [标题]

## Input Portrait
- Source type:
- Information maturity:
- Recommended mode:
- Interaction profile:
- Reliability notes:

## Context Check
- Speaker map:
- Relationship and role map:
- Scene type:
- Talk-type distinctions:
- Decision weight:
- Special notes:

## Information Gaps
- Gap 1:
- Gap 2:

## Main Topics
- Topic 1
- Topic 2
- Topic 3

## Key Signals
### Signal 1
- Source expression:
- Why it matters:
- Draft judgment:

### Signal 2
- Source expression:
- Why it matters:
- Draft judgment:

## Fact / View Split
- Objective facts:
- Interpretive views:
- Subjective guesses:
- Emotional rhetoric:

## Confidence Ladder
- Source-mentioned facts:
- Externally verified facts:
- High-confidence inferences:
- Open hypotheses:

## External Validation
- What was checked:
- What is verified:
- What remains inference:
- What remains open:

## Final Insights
- [Short, transferable judgment; list 2-5 by signal density, never pad to a fixed count]

## Business Translation
- Why this matters to us:
- Where this can be reused:
- What kind of communication or product implication it supports:

## Reusable Expressions
- Expression 1
- Expression 2
- Expression 3

## Follow-up Paths
- Research follow-up
- Card candidate
- Internal sharing use
```

Use the working memo when:

- evaluating the skill
- debugging noisy inputs
- preserving a research trace
- separating verified facts from source claims in detail

If the user asks for a final usable note, convert the working memo into the preferred final memo above.

## Notes by source type

### Livestream / podcast / dialogue

Add:

- Noise removed:
- Logic interruptions:
- Theme clusters:
- Dominant material type: fact-heavy / framework-heavy / mixed

### Interview / meeting / customer note

Add:

- Implied interests:
- Hidden constraints:
- Opportunity clues:

### Policy / article bundle

Add:

- Source hierarchy:
- Where interpretation begins:

## Quality rule

Prefer 3-5 strong signals over 20 weak observations.
If a section is thin, shorten it instead of padding it.
