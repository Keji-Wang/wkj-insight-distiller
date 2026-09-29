# Sources & Attribution

## Original work

The Insight Distiller skill — this repository's `SKILL.md`, everything under `references/`, plus the fictional `examples/` and `evals/` — is original work by **Jeffrey Wang (Keji-Wang)**, developed since June 2026 in agent-assisted consulting workflows.

The private working version runs daily on interview notes, meeting minutes, and transcripts. This public repository is the skill's own `portable-open` profile: the same analysis core, packaged without internal tooling dependencies so that any agent that can read Markdown can use it.

Upstream verification (2026-09-29): the skill's installation provenance records show no upstream repository, and a full-file review found no third-party code, prompts, rule sets, or templates inside the skill. The skill is not derived from any existing project.

## Concept credits (ideas only, no text copied)

`references/human-writing-rules.md` combines three public "AI-flavor review" lenses. The **ideas** are credited here; the word lists, rules, and wording in that file were written independently for this skill, and no text was copied from these sources:

| Lens | Source | License | How this skill uses the idea |
|---|---|---|---|
| 人味儿写作 / renwei-writing — keep the person behind the judgment | [orange2ai/renwei-writing](https://github.com/orange2ai/renwei-writing) by 橘子 (Orange) | Custom dual license (free for open-source use) | The "writing posture" rules: do less, keep the person in the text, plain words beat inflated words |
| humanizer prompt lineage — blacklist of AI sentence habits | e.g. [blader/humanizer](https://github.com/blader/humanizer) and derivatives (licenses vary by fork) | — | The approach of maintaining an explicit blacklist of recognizable AI writing patterns |
| dbs-ai-check — AI flavor as over-smoothness | [dontbesilent2025/dbskill](https://github.com/dontbesilent2025/dbskill) by dontbesilent | CC BY-NC 4.0 | The diagnostic stance: AI flavor is a sign that prose is too smooth, too complete, too evenly explained, or too eager to sound profound |

If you are one of the authors above and want the credit adjusted, please open an issue.

## Related projects by the same author

- [wkj-human](https://github.com/Keji-Wang/wkj-human) — a sibling skill that reviews and minimally rewrites AI-flavored **business writing**. Insight Distiller operates one step earlier: structuring **source material** into grounded memos. They share no code.

## Examples and evals

All material under `examples/` and `evals/` was newly written for this public release. Every person, company, and event in the examples is fictional.
