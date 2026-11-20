# Compact Run Evidence

These files preserve a small, reviewable subset of the final Problem 6
workflow evidence:

- `p6-proof-journal.jsonl` is raw structured workflow state for the proof graph,
  including normal reconciliation transitions, proved helper nodes, and the
  final target.
- `p6-final-verification.jsonl` records the final manager and project
  verification gates.

The records document the formalization and verification workflow. Absolute
source-workspace paths were replaced with
`<workspace>/IMO2026/Solution`, the published archive directory; no other
content was rewritten.

This is verification evidence, not a complete agent transcript. Exploratory
prompts, full responses, caches, credentials, and unrelated operational logs
are deliberately excluded.
