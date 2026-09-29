# Minimum Background Template

Use this template whenever the material is a multi-speaker conversation, an interview, a customer discussion, a school-enterprise exchange, or any scene where interpretation depends on speaker role and context.

## Why this exists

The biggest risk in this skill is not weak summarization.
It is interpretation drift caused by missing background.

Without minimum context, the memo can confuse:

- who was speaking
- who was leading
- who was agreeing politely
- who was correcting the frame
- what kind of scene the conversation actually was

## Minimum six fields

1. **内容类型**
- 访谈录音 / 客户沟通 / 校企交流 / 内部会议 / 直播或播客 / 单人表达

2. **讲话人映射**
- `讲话人 1/2/3` 分别是谁
- each person's name, role, and side if known
- if possible, attach one short cue line: either a short original quote or a one-line summary of what this speaker mainly said

3. **关系与角色**
- 我方与对方分别是什么关系
- customer / prospect / partner / school / internal colleague / service provider

4. **场景目的**
- 这次对话是来做什么的
- exploratory / sales / consulting diagnosis / partner discussion / internal sync / school-enterprise exchange

5. **判断权重来源**
- 以谁的表达为主
- 哪些内容更多是我方提问结构
- 哪些内容是双方往返后形成的判断

6. **特殊说明**
- 哪位同事基本没发言
- 哪段是我方刻意引导
- 哪些地方对方明确纠正过
- 哪些说法只是试探性表达

## Reusable template

```markdown
## 背景补充
- 内容类型：
- 讲话人映射：
- 讲话人识别提示：
- 关系与角色：
- 场景目的：
- 判断权重来源：
- 特殊说明：
```

## If the environment allows follow-up questions

Prefer asking these five:

1. `讲话人 1/2/3 分别是谁？`
2. `如果你一时记不清，可先看这位讲话人的一句原话或主要内容提示，再确认身份。`
3. `这次对话是什么场景？`
4. `谁是主要表达方，谁是引导方？`
5. `哪些内容是对方明确认可的？`
6. `哪些地方是你方判断、对方纠正，或尚未确认？`

Do not dump long transcript chunks.
Use only a short cue that helps recognition with low effort.

## If the environment does not allow follow-up questions

Treat this template as a front-loaded requirement.

If the fields remain incomplete:

1. show the information gaps clearly
2. lower the force of interpretation
3. avoid writing guesses as settled conclusions

## When to force this template

Force this intake when:

- multiple speaker labels appear
- the source is a meeting, interview, customer discussion, or school-enterprise exchange
- the transcript clearly contains prompting, endorsement, or correction dynamics
- the result is meant for formal reuse or forwarding
