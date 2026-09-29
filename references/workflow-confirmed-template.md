# Workflow-Confirmed Template

Use this file when adapting `insight-distiller` to messaging bots, scheduled pipelines, or any environment that supports only a short intake and a stable Markdown output.

## Goal

Protect interpretation quality without turning the workflow into a long conversation.

This profile should:

1. front-load the critical context
2. avoid repeated follow-up questions
3. produce a stable memo that can be reused quickly

## Recommended intake fields

Collect these fields up front whenever possible:

1. `source_content`
- Document link, transcript, minutes, or cleaned text

2. `content_type`
- interview / customer discussion / school-enterprise exchange / internal meeting / livestream / single-speaker material

3. `speaker_map`
- who `讲话人 1/2/3` are, if visible
- whenever possible, pair each speaker with a short cue line so the user can recognize the person without re-reading the whole transcript

4. `relationship_context`
- what each side is, and whether the scene is customer, partner, school, internal, or service-side

5. `scene_purpose`
- exploratory / diagnosis / sales / partner discussion / internal sync / other

6. `judgment_weight`
- whose expression should be treated as the main source of judgment

7. `special_notes`
- prompting, correction, weak speakers, or anything easy to misread

8. `research_mode`
- off / on-demand / required

9. `output_purpose`
- internal working memo / forwardable note / communication prep / knowledge capture

## Minimum required set

If user friction must stay low, require at least:

1. `source_content`
2. `content_type`
3. `speaker_map`
4. `relationship_context`
5. `scene_purpose`

If any of 3 to 5 are missing for a multi-speaker business conversation, lower interpretation strength automatically.

If numbered speakers appear and identity is still unconfirmed, do not write a guessed mapping into the memo.

Default behavior:

1. ask for confirmation first
2. if confirmation is unavailable, output a short confirmation block instead of a full elevated memo
3. only proceed with provisional labels if the user explicitly wants that
4. before confirmation, do not output the memo body at all

## Speaker confirmation aid

When the source uses numbered speaker labels, do not ask the user to identify people from numbers alone if you can avoid it.

Prefer this pattern:

1. show the speaker number
2. show one short original line or one-line summary of what this speaker mainly said
3. ask the user to confirm the person's identity and side

Good example:

```md
讲话人3：
- 识别提示：主要在讲学校正在做数字化转型中心，以及希望企业参与专业建设
- 请确认：这位是谁？属于哪一方？
```

Keep the cue short.
The goal is recognition, not another round of full summarization.

## Hard gate for speaker identity

When both of these are true:

1. the material is multi-speaker
2. role or identity changes interpretation

then speaker identity is a gate, not a soft suggestion.

That means:

- do not write a guessed real name, title, or side for any speaker (for example `Speaker 1 is probably their sales director`) into the formal memo
- do not say `Speaker 2 is likely the client` as if it were a confirmed mapping
- do not hide the guess inside `输入识别`

Instead:

```md
## 待确认信息
- 讲话人1：
  - 识别提示：
  - 请确认：这位是谁？属于哪一方？
```

Only after confirmation should the full memo proceed.

The required first-step shape is:

```md
## 待确认信息
- 讲话人1：
  - 识别提示：
  - 请确认：这位是谁？属于哪一方？
```

Not acceptable as a first response:

- a full memo plus a question at the end
- `输入识别` with guessed functional roles
- `说话人1（顾问侧）` or similar role guesses in any formal section

## Output expectation

Prefer:

1. a polished Markdown memo
2. a short `信息缺口` section
3. optional `可转发摘要` only when the purpose requires it

Do not default to:

1. long debug traces
2. method explanations
3. excessive research logs

## Degrade rules

### Light degrade

Use when:

- some speaker mapping is partial
- scene purpose is still broad
- judgment weight is missing but the role structure is mostly visible

Behavior:

- keep the memo structure
- soften role-based conclusions
- show the gap near the end

### Medium degrade

Use when:

- multi-speaker identity is mostly unclear
- relationship context is missing
- prompting versus endorsement is likely to be confused

Behavior:

- reduce the number of hard insights
- add a visible `以下判断为暂定分析`
- avoid attribution-heavy conclusions

This medium degrade applies only after the user explicitly allows provisional continuation.
It does not override the initial confirmation gate.

### Heavy degrade

Use when:

- noise is high
- roles are unclear
- the output is meant to be forwarded but the context is badly incomplete

Behavior:

- do not produce a fully elevated memo
- output only themes, early signals, key gaps, and suggested follow-up
