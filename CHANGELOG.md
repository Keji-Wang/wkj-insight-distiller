# Changelog

## 0.2.0 — 2026-09-30

Added a Deepening Pass (workflow step 6) between material organization and memo drafting — two self-check questions before writing:

- **Connections** (multi-document inputs only): surface echoes, contradictions, or repeated signals across the documents in the same input; label the connection as analyst interpretation, and convert guessed shared mechanisms into research questions. Explicitly scoped to the current input — no cross-session memory is claimed.
- **Missing context** (every input): flag load-bearing statements whose weight depends on background the reader may lack (policy, industry structure, organizational history); name the background type, report findings under an explicit `背景提示` label distinct from the material's internal information gaps, and convert them into research questions. Analyst-supplied background used to frame an interpretation must itself be marked unverified.

Also in this release:

- Two new fictional evals with blind-run records: `examples/09-connections` (pass), `examples/10-missing-context` (pass after two rule iterations — the iteration history is documented in `docs/validation.md`).
- README updated to describe only the blind-run-verified behaviors above (Chinese and English).

## 0.1.0 — 2026-09-29

First public release.

- Core method: input routing and information-maturity detection, speaker-identity hard gate for numbered transcripts, fact / view / interpretation / hypothesis separation, Source-Only vs Research-Enhanced modes, memo-first output template, post-write humanization pass.
- Four interaction profiles (`portable-open` as the conservative default, plus `local-interactive` / `workflow-confirmed` / `form-constrained` for adaptation).
- 8 fictional example cases with expected behavior, covering single interviews, unresolved disagreement, unknown speakers, AI-processed notes, thin material, embedded instructions, unverifiable claims, and partially readable files.
- Validation status is recorded honestly in `docs/validation.md`: structural checks and blind model trials are done; independent human review is not.
