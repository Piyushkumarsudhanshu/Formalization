# IMO 2026 — Completed Solution Archive

This directory preserves the six proof-complete IMO 2026 formalizations.
The source uses Lean 4 and Mathlib and is supported by repository, paper,
and other online documentation.

## Status

- Problems 1–6 are complete in `IMO2026/P1.lean` through
  `IMO2026/P6.lean`.
- The project has no project-local `sorry`, `admit`, custom `axiom`, or
  `unsafe` declaration.
- `lake build IMO2026` completed successfully on 30 July 2026.
- The project uses Lean `v4.32.0-rc1` and pins mathlib to
  `3b5afa97c31c95c69273cc3724eb50c78399405c`.

`SHA256SUMS` records the exact six solution modules retained from the completed
campaign.

| Problem | Retained formal result |
| --- | --- |
| P1 | Choice-independent terminal value for the gcd/lcm replacement process |
| P2 | `OM = ON` in the midpoint/circumcenter configuration |
| P3 | Liu's greatest guarantee is `2^n / (2^(n+1) - 1)` |
| P4 | The forceable angles are exactly `π / n` for natural `n ≥ 2` |
| P5 | Exactly the functions `f(x) = x + c` with `c ≥ 0` |
| P6 | Eventual additive periodicity of the least admissible gcd sequence |

## Source and Attribution

The theorem statements and initial project structure came from Joseph Myers's
Apache-2.0-licensed
[`jsm28/IMOLean`](https://github.com/jsm28/IMOLean) repository, at baseline
commit
[`3fc62b6`](https://github.com/jsm28/IMOLean/commit/3fc62b66ec02aa8446f3a1461f540ed93a74caa3).
The original copyright and license headers remain in the Lean source files.

The six Lean modules preserve the formalized problem statements and the source
repository's declaration structure.

During preparation of the source formalizations, Lazar Milikic contributed the
accepted correction to the Problem 1 move definition in
[`jsm28/IMOLean#1`](https://github.com/jsm28/IMOLean/pull/1), merged as
[`0cb21a1`](https://github.com/jsm28/IMOLean/commit/0cb21a162b3fc50c8ac85aefb47289a9ff035e2b).

## Method

The problems were formalized individually and checked with Lean and Mathlib.
Lean and mathlib searches, public repositories, papers, and general web
research were used as supporting documentation. These are documented
formalizations rather than claims of independent solution discovery.

Every completed declaration passed deterministic placeholder and kernel checks.
The six retained modules were then checked together with a clean Lake build.

The `run-evidence` directory contains a compact, path-sanitized proof journal
and final verification record for Problem 6. Raw prompts, complete transcripts,
credentials, caches, and temporary operational state are intentionally not
published.

## Reproduce

From this directory:

```bash
lake exe cache get
lake build IMO2026
```

To repeat the source-level hygiene check:

```bash
rg -n --glob '*.lean' '\b(sorry|admit|axiom|unsafe)\b' .
```

The command should produce no matches.

## License

The project is distributed under the Apache License 2.0. See `LICENSE` and the
headers in the individual source files.
