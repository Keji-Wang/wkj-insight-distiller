---
name: insight-distiller
description: >-
  Distill interviews, meeting notes, meeting minutes, livestream or podcast
  transcripts, subtitles, articles, and other outside information sources
  into source-grounded insight memos. Use when the agent needs to extract
  key themes, separate facts from opinions, identify high-value signals,
  trace the mechanism behind a phenomenon, or turn noisy raw material into
  reusable judgments, talking points, or forwardable notes. Supports both
  source-only and research-enhanced execution, and handles multi-speaker
  material by confirming speaker roles, relationship context, and scene
  meaning before drawing strong conclusions.
---

# Insight Distiller

Turn messy outside information into reusable judgment assets.
Start from the source, extract the signal, decide what needs verification, and only then elevate it into a memo that can be reused in communication, research, or knowledge capture.

## Workflow

1. Identify the input type and information maturity.
Read [references/input-routing.md](references/input-routing.md).

2. Choose the execution mode.
- **Source-Only**: Use when the user wants a fast first-pass extraction from the material itself, or when the topic is mostly conceptual, historical, or not time-sensitive.
- **Research-Enhanced**: Use when the content depends on current policy, regulation, markets, geopolitics, industry shifts, or other unstable outside facts. Read [references/research-trigger.md](references/research-trigger.md).

3. Choose the interaction profile.
Read [references/version-profiles.md](references/version-profiles.md).
- Default to `portable-open` when you cannot determine the environment. It is the conservative, low-dependency profile this public version is built around.
- Use `local-interactive` when you can ask follow-up questions naturally.
- Use `workflow-confirmed` when the environment supports only a small number of confirmations.
- Use `form-constrained` when the environment mainly accepts one-shot text, attachments, or links.
- If using `workflow-confirmed`, also read [references/workflow-confirmed-template.md](references/workflow-confirmed-template.md).

4. Run a context intake gate for multi-speaker material.
- If the source is a meeting note, interview, customer discussion, school-enterprise exchange, or any multi-speaker transcript, read [references/conversation-context-check.md](references/conversation-context-check.md).
- Use [references/minimum-background-template.md](references/minimum-background-template.md) as the minimum background set.
- In `local-interactive`, ask only the missing context that changes interpretation.
- In `workflow-confirmed`, front-load the critical fields and keep confirmations short.
- In `form-constrained` or `portable-open`, do not fake certainty. Surface information gaps before strong interpretation.
- If numbered speakers appear and identity affects interpretation, treat speaker mapping as a gate. Do not write guessed names, titles, or sides into the formal memo.
- When the mapping is still missing, output a short `待确认信息` block first. Only proceed with provisional labels after the user explicitly allows it.

4.1 Hard stop for unconfirmed numbered speakers.
- If the material uses `讲话人 1/2/3/4` style labels and those identities would change interpretation, do not produce any insight body before confirmation.
- The first response should be only a `待确认信息` block plus the minimum explanation needed for why confirmation is required.
- Do not output `输入识别`, `洞察一`, `核心判断`, or any other elevated memo section before that confirmation step is satisfied.
- The only exception is when the user explicitly says to continue without waiting. In that case, mark the analysis as provisional and keep the speakers unnamed.

5. Preprocess the source before insight work.
- Strip noise for livestreams, podcasts, and messy transcripts.
- If the input is a dialogue-heavy subtitle file, read [references/livestream-preprocess.md](references/livestream-preprocess.md).
- Separate facts, views, guesses, and emotional rhetoric.
- Cluster themes before synthesizing judgments.

6. Run a deepening pass before writing the memo.
After the material is organized and before drafting the memo body, ask two questions.
The two questions have different applicability: Connections applies only when the input contains more than one document; Missing context applies to every input, including single documents.
Output findings only when the material genuinely supports them — this pass is an optional memo module, never a mandatory section, and "nothing to add" is a valid result.

- **Connections (across sources within this input)**: when the input contains more than one document, check whether the sources echo, contradict, or repeatedly signal the same thing. When a connection is worth reporting, present it as the analyst's interpretation — a possible shared mechanism behind the signals — not as an established fact. If the shared mechanism is only a guess, convert it into a research question instead of asserting it. Scope limit: connections run across the documents in the current input only. This skill has no cross-session memory; never promise or imply automatic linking to past interviews or earlier material.

- **Missing context (analyst background gaps)**: apply to every input. A practical test: for each load-bearing statement, ask whether a reader with no knowledge beyond the text would still grasp why the statement matters. If the importance depends on outside context — whether a policy direction exists, how significant a regulatory, industry, or organizational move is, what its history implies — that is a missing-context finding, even when the speaker already mentioned part of the background in passing. For each finding: name the type of background needed to fully understand the statement, then turn it into a research question. Report findings under an explicit background-gap label (such as a `背景提示` item or section) so they do not blur into the material's internal information gaps. Background knowledge you yourself use to frame an interpretation — e.g. calling an industry "policy-driven" — is outside the source: label it as analyst-supplied and unverified, or convert it into a research question. If research capability is available, the question may go through the Research-Enhanced flow; verified results are labeled `externally supported fact`, never mixed into source expression.

Keep this pass distinct from existing sections:
- `信息缺口 / Information Gaps` and the follow-up signals section describe information missing **inside the material**.
- Missing context here describes background knowledge missing **on the analyst's or reader's side** — a statement can be fully supported by the material and still depend on outside background for its weight to register.
- Both findings use the standard labeling: they are `analyst interpretation`, and their research questions belong with the other follow-up signals.

7. Produce the memo first.
Read [references/output-template.md](references/output-template.md).
Read [references/human-writing-rules.md](references/human-writing-rules.md).
Default output is a Markdown memo, not a card.
Prefer an insight-first memo for the main deliverable.
Keep heavy verification details in a short appendix when needed instead of letting proof structure dominate the reading experience.

8. Run a post-write humanization pass.
- Apply [references/human-writing-rules.md](references/human-writing-rules.md) as one combined lens: keep the person behind the judgment visible, do less, and do not polish every sentence into a performance.
- Remove inflated significance, promotional words, rule-of-three rhythm, vague authority phrases, and other recognizable AI fingerprints.
- Treat AI flavor as a sign that the prose is too smooth, too complete, too evenly explained, or too eager to sound profound.
- Only humanize sentences you wrote. Do not distort source facts or quoted expressions just to sound less AI-like.

9. Create derivative outputs only after the memo is solid.
- Talking points
- Internal sharing notes
- Card candidates
- Research questions
- Knowledge-base entries

## Core judgment rules

Always keep these boundaries visible:

1. `source expression`
2. `analyst interpretation`
3. `externally supported fact`
4. `open hypothesis`

Do not treat raw recordings, livestream clips, subtitles, or AI-generated minutes as mature truth objects.
Treat them as phenomenon records that may contain:

- reliable first-hand signals
- selective memory
- framing effects
- rhetorical overstatement
- mistaken factual claims
- narrative details added by a summarizer rather than said in the original scene

The goal is not automatic debunking.
The goal is to extract the valuable claim, trace the likely mechanism behind it, and then decide what deserves external support.

## Input recognition

Always identify both:

1. **Input container**
- Platform documents (e.g. Feishu Docx, Google Docs exports)
- Platform meeting minutes or AI smart summaries
- Local Markdown or plain text
- Raw transcript
- Livestream or podcast subtitles
- Article bundle

2. **Information maturity**
- Raw material
- Semi-structured notes
- Already summarized or AI-processed material

3. **Context sufficiency**
- Speaker clarity
- Relationship clarity
- Scene clarity
- Whether the endorsement or correction chain is visible

If the material is a messy transcript or livestream, treat preprocessing as mandatory, not optional.
If the material has already been summarized or rewritten by another AI, treat its narrative details as unverified until they can be traced back to a source.

## Source-Only mode

When using Source-Only mode, do not jump to big conclusions too early.
Do not mistake repeated emphasis for real insight density.

Produce these in order:

1. Material portrait
2. Theme map
3. Fact and view split
4. Confidence ladder
5. Signal list
6. Draft judgments
7. Business translation

Prefer fewer, harder judgments over long lists of weak observations.

## Research-Enhanced mode

When the content depends on unstable outside facts, do not rely only on source interpretation.
If your environment has no research or search capability, stay in Source-Only mode, label strong factual claims as `未核实 / unverified`, and rewrite them as research questions instead of inventing citations.

For each high-value signal:

1. Rewrite it as a research question.
2. Decide what kind of source should verify it.
3. Prefer primary and official sources when possible.
4. Distinguish:
- verified facts
- high-confidence inferences
- open hypotheses

Do not hide uncertainty.
If something is only a plausible explanation, label it clearly.

## Material-specific rules

### Interviews and meeting notes

- Focus on signals, interests, positioning, practical constraints, and what the speaker reveals indirectly.
- Extract implications for business, talent, policy, or execution.
- Clearly separate:
  - what the speaker actually said
  - what the analyst inferred from the source
  - what was externally supported afterward
- If a strong sentence in the memo is mainly the analyst's synthesis, do not let it read as if it were the speaker's original statement.
- If the discussion depends on who was leading, probing, correcting, endorsing, or barely speaking, make that structure explicit before drawing conclusions.

### Livestreams, podcasts, and dialogue transcripts

- Remove greetings, thanks, technical interruptions, gift acknowledgements, and repetitive chatter.
- Identify concept-building, framework-building, and transferable judgments.
- Keep separate buckets for `source claim` and `real-world verified fact`.
- Mark `logic interrupted` when a clipped segment breaks the chain.

### Policy and industry materials

- Separate the stated policy intention from likely implementation implications.
- Prefer source-grounded interpretation before commentary.

## Default deliverable

Use the memo as the default output.
Use cards only as a second-step derivative.

Prefer this delivery order:

1. A clear insight memo that reads like a finished internal note.
2. A short verification appendix only if the topic is time-sensitive or contested.
3. Derivative outputs such as cards or talking points.

When useful, support two audience modes:

1. **Internal working audience**
- Can keep stronger judgments.
- Can mention the recording or minutes nature of the source.
- Can keep what still needs checking.

2. **Forwardable audience**
- Remove obvious recording artifacts, AI-summary wording, and process clutter.
- Keep only judgments the user is comfortable circulating internally.
- Prefer shorter, cleaner phrasing suitable for leaders, partners, or forwarded memos.

## Optional integrations (none required)

This skill is plain Markdown with no hard dependencies. It works on pasted text or local text files alone. If your environment has them, these integrate well:

- **Document fetching** (e.g. `lark-doc`, `lark-minutes` for Feishu Docs and meeting minutes): use to pull source material. Without them, ask the user to paste or export the text.
- **External research** (web search or a research skill): enables Research-Enhanced mode. Without research capability, stay Source-Only, mark claims `未核实 / unverified`, and never fabricate citations.
- **Card generation** (e.g. `ljg-card`): turn a mature memo into visual cards as a derivative.
- **Writing-review skills** (e.g. `renwei-writing`, `dbs-ai-check`): sharper post-write review. See [SOURCES.md](SOURCES.md) for the ideas this skill borrowed from them.

## Output rule

Always favor grounded judgment over elegant phrasing.
If a sentence sounds good but is not anchored in the source or verified context, cut it.

Avoid obvious AI writing patterns in the final memo:

- Do not inflate ordinary facts into turning points, signals of an era, or broader landscapes unless the source and evidence truly support it.
- Do not rely on `不是 X，而是 Y`, repeated three-part lists, or every-paragraph gold-line endings.
- Do not smooth away all uncertainty, friction, or half-resolved tension.
- Do not use promotional, consultancy-demo, or abstract strategy language when a plainer sentence would do.
- Do not over-edit away the author's or analyst's natural handprint.

Prefer:

- fewer but harder judgments
- plain statements before conceptual packaging
- one real memorable line over paragraph-by-paragraph rhetorical performance
- concrete risk, mechanism, or constraint over abstract uplift
- clear boundaries between source expression and analyst synthesis
- one compressed high-value warning over repeated low-value reminders

Do not output generic inspiration language.
Do not call something an insight unless it has either:

1. a clear source-grounded mechanism, or
2. a clear external verification path
