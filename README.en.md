# Insight Distiller

[中文](README.md) | English [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**Turns interviews, meeting notes, transcripts, and articles into insight memos where every judgment carries a source-type label — source expression, analyst interpretation, verified fact, or open hypothesis — designed to be traceable and checkable.**

> First be honest about what the material is; then decide what can be read out of it.

It does not promise "automatic truth extraction" or "zero hallucination": the skill organizes judgment; verification stays with you.

## Quick start

Pure Markdown, no dependencies. Any AI Agent that can read local files (or accept pasted long text) can use it.

```bash
git clone https://github.com/Keji-Wang/wkj-insight-distiller.git
cp -r wkj-insight-distiller ~/.claude/skills/insight-distiller
```

Other agent platforms: put `SKILL.md` together with the `references/` directory into the platform's skill directory (the directory structure must stay intact — SKILL.md references `references/` by relative path). cc-switch users can install directly from this repository. Platforms not individually tested are not claimed as compatible.

Once installed, paste material or give a local file path, e.g. "Here is an interview transcript; please organize it into an insight memo".

## A real blind-run example (fictional input + actual model output)

The following is quoted from [examples/01-single-interview/](examples/01-single-interview/) in this repository: the material is entirely fictional; the output was generated in one pass by a model that had read only SKILL.md and had no access to any expected answers. The excerpts are unedited and quoted verbatim in Chinese from the repository files.

**Input (excerpt of the material):**

> 【虚构演示】以下是一次单人访谈的整理稿。受访者：林若楠，独立书店"青梧书店"主理人。
>
> **问**：先聊聊你怎么从景区店走到社区店的吧。
>
> **林若楠**：2019 年我在青澜湾景区商圈开了第一家店，六十多平，主打旅游客群和文创。头一年半还行，真正的转折是 2023 年——景区客流肉眼可见地往下掉，租金反而涨了四成，我算了一下账，撑不下去，年底把景区店关了。
>
> **问**：那时候有考虑过彻底不做了吗？
>
> **林若楠**：说实话想过。但我不甘心，后来在老城区的梧桐里社区找了个小铺面，重新开。刚搬过来的时候很惨，一天进店的人不到二十个。我就开始在小区业主群里做读书活动，一开始就七八个人来。现在社群里有一千八百多人，周末活动的上座率能到八成。
>
> **问**：收入结构有变化吗？
>
> **林若楠**：变化特别大。景区店的时候，卖书占总收入的七成。现在书只占四成左右，咖啡和活动加起来过半。去年办了三十多场活动，哦不对，应该是四十场上下，周末基本每周一场。

**Output (one insight from the blind-run memo):**

> ### 洞察：这家店活下来靠的是收入结构换轨——书从七成降到四成，咖啡和活动接过一半以上
>
> #### 现场现象
> - 景区店时期，卖书占总收入的七成
> - 社区店现在：书只占四成左右，咖啡加活动合计过半
> - 去年办了约四十场活动（受访时从“三十多场”改口），周末基本每周一场，上座率八成
>
> #### 核心判断
> 她把一家零售生意做成了空间运营生意。书还在卖，但已不是收入主体；真正的营收来自咖啡（空间时间的变现）和活动（社群关系的变现）。“书店的本质是邻里公共客厅”不只是一句理念，她的账本结构就是在按这句话运营。
>
> #### 外部佐证
> - 本轮未做外部验证。核验路径：她本人的分项收入与毛利数据；其他社区书店的公开财务案例
>
> #### 这条洞察的意义
> 评估任何实体空间转型，先看收入结构，再看选址故事。收入结构换了，才说明模式真的换了；只换位置不换结构，多半只是把旧模式搬到新地方。

(Each insight follows this four-part structure: observed phenomena → core judgment → external evidence → significance. Two details worth noting: the material's self-correction — "三十多场" changed to "四十场上下" — is honestly labeled as "约四十场（受访时改口）" instead of being silently rounded; and the interviewee's industry claim that "the future of bookstores is definitely in communities" is labeled in the full output as an "n=1 survivor extrapolation", not as an industry fact. Full input and output: [examples/01-single-interview/](examples/01-single-interview/).)

## It also refuses to output: when speaker identity is unknown

**Input**: a transcript of a three-party conversation where speakers are only labeled 「讲话人1/2/3」 with no name mapping.

**Actual model output**: no memo body at all — it stops and asks for confirmation first:

> 按规则，编号讲话人身份未确认前，我不把猜测的名字或立场写进正式产出。

(The full output is a confirmation table containing only cue lines and confirmation requests; analysis starts only after the mapping is confirmed. Full blind run: [examples/03-unknown-speakers/](examples/03-unknown-speakers/). This skill's value is not "summarizing more beautifully" — it is knowing when not to summarize.)

## 30-second understanding: input → what it does → output

- **Input**: interview write-ups, meeting minutes (human or AI generated), livestream/podcast transcripts, subtitle files, article bundles, information-poor fragments; pasted text or local files both work.
- **What it does**: first identifies input type and information maturity, and separates facts, opinions, inferences, and hypotheses; multi-speaker material goes through speaker confirmation first; without research tools it labels claims "unverified" honestly, and takes responsibility only for the part of a file it actually read.
- **Output**: one Markdown insight memo — input recognition, information gaps, insights (observed phenomena / core judgment / external evidence / significance), signals worth digging into, directly reusable expressions, plus an optional forwardable summary. The number of insights follows signal density — fewer, harder judgments over padded lists.
- **Two modes**: Source-Only (default, material only) and Research-Enhanced (external verification of time-sensitive claims when search is available).

## The problem it solves

Handing an interview or meeting transcript to an AI typically produces a summary that "reads smoothly": disagreements are sanded flat, guesses are written as facts, generic speaker labels get assigned invented names and stances, and narrative details added by an AI summarizer get treated as things that actually happened. The messier the material, the worse this gets.

The two blind-run examples above are the corresponding behavior designs: number conflicts labeled honestly, industry claims downgraded to the speaker's opinion, speakers confirmed before analysis, and no pretending that unverified means verified. The four-way source boundary (source expression / analyst interpretation / verified fact / open hypothesis) runs through all output — making "who said this / this is my inference / this is unverified" explicit, and leaving the remaining judgment to a human.

## Examples and validation

[examples/](examples/) contains 8 fictional cases (all people, companies, and figures are invented), covering the scenarios where this skill is most likely to go wrong; each case includes the input, expected behavior, and one real blind-run output. Validation status is published honestly in [docs/validation.md](docs/validation.md): 8 blind runs, 7 pass, 1 partial pass, 0 fail; **independent human review is not done yet** — this version should not be treated as stable.

## Limitations

- Behavior depends on the executing model's own capabilities: the same skill performs differently across models; systematic trials were run on GLM only (see validation.md);
- Tuned for Chinese business material; English material is not systematically validated;
- It organizes judgment, it does not replace verification: content marked "unverified" still needs human checking;
- "Core judgments" in the memo remain the analyst's product — what the skill delivers is traceability of every judgment, not their correctness.

## Sources & acknowledgments

This skill is original work (upstream verification record in [SOURCES.md](SOURCES.md)). The writing-review layer in `references/human-writing-rules.md` draws on three public "AI-flavor review" lenses as concepts (renwei-writing, the humanizer lineage, dbs-ai-check), with no text copied. Sibling project by the same author: [wkj-human](https://github.com/Keji-Wang/wkj-human) (reviews and minimally rewrites AI-flavored business writing — operates downstream of this skill).

## Author & contact

- Author: Jeffrey Wang ([Keji-Wang](https://github.com/Keji-Wang))
- X: [@JiafuWang](https://x.com/JiafuWang)
- Questions and suggestions: please prefer [Issues](https://github.com/Keji-Wang/wkj-insight-distiller/issues)

## License

[MIT](LICENSE) © 2026 Jeffrey Wang (Keji-Wang). Examples and test materials are entirely fictional; please never submit real interviews or client material to this repository (see [CONTRIBUTING.md](CONTRIBUTING.md)).
