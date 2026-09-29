# Conversation Context Check

Use this file before analyzing interviews, meeting notes, customer calls, school-enterprise exchanges, or any multi-speaker transcript.

## Why this matters

Conversation material is easy to misread.

Typical distortions:

- treating the user's probing question as the counterpart's real position
- treating polite agreement as substantive endorsement
- missing where the counterpart corrected or limited the user's framing
- assuming a generic vendor-buyer context when the scene is actually a cross-organization collaboration (for example a service team working with a school)
- treating all speakers as equal when one person barely spoke and another held the real decision power

If these are not clarified early, the memo may sound sharp but still be wrong.

## Trigger conditions

Run this check when any of the following are true:

- the source has `讲话人 1/2/3` style labels
- the transcript involves more than one organization
- the user was actively guiding, prompting, or testing ideas
- the counterpart agreed in some places but corrected in others
- the user's organization type changes the meaning of the discussion
- the memo would rely on role power, authority, or endorsement level

## Minimum background set

Read [minimum-background-template.md](minimum-background-template.md) and confirm only the missing items that would change interpretation.

The minimum set is:

1. speaker map
2. relationship and role map
3. scene type or conversation purpose
4. talk-type distinctions
5. decision weight
6. special notes

## By interaction profile

### Local-interactive

Ask short follow-up questions before strong interpretation.

Good default questions:

1. `讲话人 1/2/3 分别是谁，属于哪一方？如果编号本身不够辨认，先附一句原话或主要内容提示再请用户确认。`
2. `这次对话是什么场景，是访谈、需求沟通、校企交流，还是内部讨论？`
3. `哪些内容是你在引导，哪些是对方明确认可，哪些地方对方有纠正或保留？`

Ask only what changes meaning. Do not turn intake into a long interview.

### Workflow-confirmed

Front-load the minimum background set as fields or a short confirmation step.

Preferred behavior:

1. require speaker mapping when visible
2. if speaker numbers are ambiguous, show a short cue line for each key speaker before asking for confirmation
3. require scene type
4. require relationship context
5. optionally ask for one special note if there is likely distortion risk
6. if speaker identity remains unconfirmed and affects interpretation, stop at a short `待确认信息` block instead of continuing with guessed identities

### Form-constrained or portable-open

Do not fake certainty when context is missing.

Instead:

1. mark speaker mapping as partial or unknown
2. mark role-based judgments as provisional
3. add an `信息缺口` section near the top of the memo
4. avoid sentences that imply endorsement or authority unless the source clearly supports them
5. never convert numbered speakers into guessed named identities unless the user confirms them

## Talk-type distinctions

For many business or interview materials, separate these buckets when needed:

- your probing or framing
- counterpart confirmation
- counterpart correction or pushback
- analyst synthesis after the fact

This matters because a sharp memo often fails not on writing quality, but on misattributing one bucket to another.

## Output implications

If the context check reveals important asymmetry, reflect it early in the memo.

Useful patterns:

- `以下判断里，有些是我方在引导问题，有些才是对方真正认可的内容，这两层需要分开看。`
- `这不是一次常规采购洽谈，而是服务团队与学校侧围绕合作项目的沟通，解读口径应随之调整。`
- `讲话人 3 在原始记录中发言很少，以下结论不基于其立场展开。`

## Good default

For this skill, it is usually better to ask 3 short context questions early than to output 3 pages of sharp but distorted interpretation later.

For workflow-style use, extend that one step further:

If numbered speakers are central to the meaning, it is usually better to stop and request confirmation than to proceed with guessed identities.
