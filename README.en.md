# Insight Distiller

[中文](README.md) | English

**An Agent Skill that turns interviews, meeting notes, transcripts, and articles into source-grounded insight memos — where every claim can be traced back to its source.**

把访谈、会议纪要、转录和文章，整理成每句话都能回到出处的洞察备忘录的 Agent Skill — separating what was said, what is inferred, what is verified, and what remains open.

---

## The problem it solves

Handing an interview or meeting transcript to an AI typically produces a summary that "reads smoothly": disagreements are sanded flat, guesses are written as facts, generic speaker labels get assigned invented names and stances, and narrative details added by an AI summarizer get treated as things that actually happened. The messier the material, the worse this gets.

Insight Distiller takes the opposite approach: **first be honest about what the material is, then decide what can be read out of it.**

- **Four-way boundary**: source expression / analyst interpretation / verified fact / open hypothesis, never mixed;
- **Speaker hard gate**: when material only labels speakers as `讲话人 1/2/3` and identity changes the interpretation, the skill stops and asks for confirmation first — no guessed names, no guessed sides, no memo body;
- **Disagreement is not merged**: opposing positions stay opposing; no "the team reached consensus";
- **AI-processed material is downgraded**: narrative flourishes added by a summarizer are stripped and flagged, not treated as facts;
- **No research tools means honest labels**: strong factual claims get marked `unverified / 未核实` and converted into checkable questions — citations are never invented;
- **Partial reads take responsibility only for what was read**: if only 20% of a file loaded, the memo says so up front, lists what was missed, and notes how conclusions might change.

It does not promise "automatic truth extraction" or "zero hallucination" — quite the opposite: its core value is making "who said this / this is my inference / this is unverified" explicit, and leaving the remaining judgment to a human.

## Quick start

Pure Markdown, no dependencies. Any AI Agent that can read local files (or accept pasted long text) can use it.

**Install (Claude Code / any agent with a skills directory):**

```bash
git clone https://github.com/Keji-Wang/wkj-insight-distiller.git
cp -r wkj-insight-distiller ~/.claude/skills/insight-distiller
```

Other agent platforms: put `SKILL.md` together with the `references/` directory into the platform's skill directory (the directory structure must stay intact — SKILL.md references references/ by relative path). cc-switch users can install directly from this repository. Platforms not individually tested are not claimed as compatible.

**Usage**: submit material directly to an agent with this skill installed — paste text or give a local file path — for example:

> Here is an interview transcript; please organize it into an insight memo: (material or path)

Multi-speaker material without a speaker map will first receive a confirmation block; only after identities are confirmed does the full memo get produced. To see the behavior before installing, read [examples/03-unknown-speakers/](examples/03-unknown-speakers/) (hard-gate demo) and [examples/06-embedded-instruction/](examples/06-embedded-instruction/) (embedded-instruction resistance demo).

## Inputs and outputs

**Inputs**: interview write-ups, meeting minutes (human or AI generated), livestream/podcast transcripts, subtitle files, article bundles, information-poor fragments. Pasted text or local text files both work.

**Default output**: a Markdown insight memo — input recognition, information gaps, insights (each with observed phenomena / core judgment / external evidence / significance), signals worth digging into, directly reusable expressions, plus an optional forwardable summary. The number of insights follows signal density — fewer, harder judgments over padded lists.

**Two execution modes**: Source-Only (default, material only) and Research-Enhanced (external verification of time-sensitive claims when search is available). Without research tools it stays Source-Only and labels claims honestly.

## Examples and validation

[examples/](examples/) contains 8 fictional cases (all people, companies, and figures are invented), covering the scenarios where this skill is most likely to go wrong; each case includes the input, expected behavior, and one real blind-run output. Validation status is published honestly in [docs/validation.md](docs/validation.md): 8 blind runs, 7 pass, 1 partial pass, 0 fail; **independent human review is not done yet** — this version should not be treated as stable.

## Limitations

- Behavior depends on the executing model's own capabilities: the same skill performs differently across models; systematic trials were run on GLM only (see validation.md);
- Tuned for Chinese business material; English material is not systematically validated;
- It organizes judgment, it does not replace verification: content marked "unverified" still needs human checking;
- "Core judgments" in the memo remain the analyst's product — the skill guarantees judgments are traceable, not that they are correct.

## Sources & acknowledgments

This skill is original work (upstream verification record in [SOURCES.md](SOURCES.md)). The writing-review layer in `references/human-writing-rules.md` draws on three public "AI-flavor review" lenses as concepts (renwei-writing, the humanizer lineage, dbs-ai-check), with no text copied. Sibling project by the same author: [wkj-human](https://github.com/Keji-Wang/wkj-human) (reviews and minimally rewrites AI-flavored business writing — operates downstream of this skill).

## Author & contact

- Author: Jeffrey Wang ([Keji-Wang](https://github.com/Keji-Wang))
- X: [@JiafuWang](https://x.com/JiafuWang)
- Questions and suggestions: please prefer [Issues](https://github.com/Keji-Wang/wkj-insight-distiller/issues)

## License

[MIT](LICENSE) © 2026 Jeffrey Wang (Keji-Wang). Examples and test materials are entirely fictional; please never submit real interviews or client material to this repository (see [CONTRIBUTING.md](CONTRIBUTING.md)).
