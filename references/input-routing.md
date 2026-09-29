# Input Routing

Use this file to decide how to handle the incoming material before writing any memo.

## Step 1: Identify the container

- **Platform documents** (Feishu Docx, Google Docs exports, and similar): structured documents, usually already summarized or edited.
- **Platform meeting minutes / AI smart summaries**: AI-structured meeting artifacts; useful but not fully reliable.
- **Local Markdown or plain text**: may be raw transcript, cleaned notes, or memo draft.
- **Raw transcript / subtitles**: highest noise, richest original signal.
- **Article bundle**: usually cleaner, but may mix fact and commentary.

If the material sits behind a platform and you have a document-fetching integration, use it; otherwise ask the user to paste or export the text. Never invent content for material you cannot read.

## Step 2: Identify information maturity

- **Raw**: timestamped transcript, subtitles, rough notes.
- **Semi-structured**: AI minutes, cleaned transcript, grouped notes.
- **Structured**: memo, outline, manually summarized note.

## Step 3: Check whether the scene is easy to misread

Look for these risk markers:

- more than one speaker
- placeholder labels such as `讲话人 1/2/3`
- more than one organization involved
- strong prompting by the user side
- partial agreement mixed with correction
- a scene where role power or authority changes the meaning

If any of these appear, run [conversation-context-check.md](conversation-context-check.md) and use [minimum-background-template.md](minimum-background-template.md).

## Step 4: Route by material type

### Raw transcript / livestream / podcast

Do this first:

1. Remove chatter, thanks, technical interruptions, repeated filler.
2. Identify topic shifts.
3. Cluster segments by theme.
4. Separate `source-mentioned fact` from `speaker interpretation`.
5. Mark broken chains as `logic interrupted`.
6. If the material contains current politics, finance, policy, school programs, or institutional rumors, do source cleanup before external research. Do not search until the claims are rewritten into verifiable questions.

### Interview / meeting note

Do this first:

1. Identify participants and role positions if visible.
2. If role or scene context would change interpretation, run the context check.
3. Extract what was actually said versus what is inferred.
4. If needed, separate:
- user probing
- counterpart confirmation
- counterpart correction
- analyst synthesis
5. Highlight indirect signals:
- hidden constraints
- resource gaps
- policy dependence
- demand clues
- talent clues

### Structured memo or article bundle

Do this first:

1. Detect whether it is already interpretive.
2. Separate source facts from author framing.
3. Detect whether an AI summarizer added narrative details that may not come from the original scene; mark such details as unverified until traced back to a source.
4. Avoid re-summarizing what is already concise.

## Step 5: Choose the interaction profile

Read [version-profiles.md](version-profiles.md) and pick the lightest profile that still protects interpretation quality.

- `portable-open`: the conservative default when the environment is unknown; keep logic low-dependency.
- `local-interactive`: Ask short follow-up questions when critical context is missing.
- `workflow-confirmed`: Collect a small set of required fields up front and allow at most light confirmation.
- `form-constrained`: Work mainly from what is submitted in one pass; if context is missing, surface gaps instead of hard guesses.

## Step 6: Decide whether the source is enough

Stay in Source-Only mode when:

- the request is to extract themes, viewpoints, logic, or reusable expressions
- the topic is mostly conceptual or historical
- the user wants a fast first-pass insight

Escalate to Research-Enhanced mode when:

- the source refers to current policy, regulation, news, industry shifts, school program changes, geopolitics, or market conditions
- the source makes strong factual claims but only cites rumors, screenshots, or second-hand reports
- the user wants harder judgments for communication, strategy, or public-facing reuse

If your environment has no research capability, stay in Source-Only mode and label strong factual claims as unverified instead of inventing citations.

## Step 7: Set the fallback behavior

If critical context is still missing after the available intake path:

1. name the missing information clearly
2. lower the strength of interpretation
3. separate what is source-grounded from what is provisional
4. avoid role-based or endorsement-based claims that the source cannot support
