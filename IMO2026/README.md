# IMO 2026 Lean Formalizations

This directory contains two independently retained Lean 4 archives for the
six problems of the 2026 International Mathematical Olympiad:

- [`Solution/`](Solution) — proof-complete formalizations.
- [`Formalization/`](Formalization) — an incomplete draft archive.

Both archives use the same Lake project name, `IMO2026`, and preserve the
source structure and attribution from the upstream
[jsm28/IMOLean](https://github.com/jsm28/IMOLean) project.

> [!IMPORTANT]
> Use [`Solution/`](Solution) when compiling or citing the completed
> formalization set. Do not interpret the files in [`Formalization/`](Formalization)
> as a proof-complete solution set.

## Contents

| Directory | Status | Intended use |
| --- | --- | --- |
| [`Solution/`](Solution) | P1–P6 proof complete | Reproduction, review, and downstream use |
| [`Formalization/`](Formalization) | P1–P6 draft archive; P3/P4/P6 incomplete | Review of incomplete formalizations and retained verification evidence |

## Completed Solution Archive

The [`Solution/`](Solution) archive contains one retained module for each
problem:

| Module | Formalized result |
| --- | --- |
| [`P1.lean`](Solution/IMO2026/P1.lean) | The gcd/lcm replacement process has a choice-independent terminal value |
| [`P2.lean`](Solution/IMO2026/P2.lean) | In the midpoint/circumcenter configuration, `OM = ON` |
| [`P3.lean`](Solution/IMO2026/P3.lean) | Liu's greatest guarantee is `2^n / (2^(n+1) - 1)` |
| [`P4.lean`](Solution/IMO2026/P4.lean) | The forceable angles are exactly `π / n` for natural `n ≥ 2` |
| [`P5.lean`](Solution/IMO2026/P5.lean) | Exactly the functions `f(x) = x + c` with `c ≥ 0` |
| [`P6.lean`](Solution/IMO2026/P6.lean) | The least admissible gcd sequence is eventually additively periodic |

The six modules are imported together by
[`IMO2026.lean`](Solution/IMO2026.lean). The project has no project-local
`sorry`, `admit`, custom `axiom`, or `unsafe` declaration.

### Build the completed solution

Prerequisites:

- [Lean 4](https://lean-lang.org/)
- Lake, which is distributed with the Lean toolchain
- Network access during the initial dependency download

The toolchain is pinned to `leanprover/lean4:v4.32.0-rc1`, and mathlib is
pinned to commit `3b5afa97c31c95c69273cc3724eb50c78399405c`.

From the repository root in PowerShell:

```powershell
Set-Location .\IMO2026\Solution
lake exe cache get
lake build IMO2026
```

The first command downloads prebuilt dependencies. The second builds the
canonical project target. A successful build is the primary reproducibility
check for the completed archive.

### Verify placeholder hygiene

Run this command from [`Solution/`](Solution):

```powershell
rg -n --glob '*.lean' '\b(sorry|admit|axiom|unsafe)\b' .
```

The command should produce no matches. The check is intentionally source-level:
it detects project-local proof placeholders and untrusted declarations before
the Lean kernel and Lake build provide the final verification.

### Reproducibility evidence

[`Solution/SHA256SUMS`](Solution/SHA256SUMS) lists checksums for the retained
solution modules. [`Solution/run-evidence/`](Solution/run-evidence) contains the
compact Problem 6 proof journal and final verification record.

The solution archive was developed through mathematical formalization with
Lean, Mathlib, source repositories, papers, and other online documentation.
It is a documented formalization effort, not a claim of independent solution
discovery.

## Stopped Formalization Draft

[`Formalization/`](Formalization) preserves an incomplete draft archive rather
than a completed proof set.

| Problem | Retained status |
| --- | --- |
| P1 | Complete |
| P2 | Complete |
| P3 | Two local proof obligations remain in `result` |
| P4 | The final `result` is rejected with a hard type mismatch |
| P5 | Complete |
| P6 | Three declarations remain unresolved |

The P3 archive retains two `sorry` declarations. P6 retains three unresolved
declarations: `backward_affine_rigidity`,
`globalize_eventual_affine_period`, and `result`. P4 contains no placeholder,
but it gives a winning guarantee for `π / n` where the target requires
`π / (n + 1)`.

Do not use this archive to claim completion of IMO 2026 P3, P4, or P6.

### Inspect the stopped draft

```powershell
Set-Location .\IMO2026\Formalization

# Inventory placeholder declarations
rg -n --glob '*.lean' '\b(sorry|admit|axiom|unsafe)\b' .

# Attempt the Lake build used for the draft archive
lake exe cache get
lake build IMO2026
```

The Lake build is expected to fail at P4. P1, P2, P3, P5, and P6 elaborate;
P3 and P6 do so only because Lean admits the retained placeholders.

[`Formalization/run-evidence/`](Formalization/run-evidence) contains a
summary of the draft and its verification lessons. [`Formalization/SHA256SUMS`](Formalization/SHA256SUMS)
records the exact ten retained Lean modules.

## Repository Layout

```text
IMO2026/
├── README.md
├── Formalization/
│   ├── IMO2026.lean
│   ├── IMO2026/
│   │   ├── P1.lean through P6.lean
│   │   └── P2Helpers.lean, P3Helpers.lean, P4Helpers.lean,
│   │       P6Helpers.lean
│   ├── run-evidence/
│   ├── lakefile.toml
│   ├── lake-manifest.json
│   ├── lean-toolchain
│   └── SHA256SUMS
└── Solution/
    ├── IMO2026.lean
    ├── IMO2026/
    │   └── P1.lean through P6.lean
    ├── run-evidence/
    ├── lakefile.toml
    ├── lake-manifest.json
    ├── lean-toolchain
    └── SHA256SUMS
```

The `lake-manifest.json` files pin the resolved package graph. `lakefile.toml`
pins mathlib and the Lean REPL dependency.

## Source and Attribution

The theorem statements and initial project structure came from Joseph Myers's
Apache-2.0-licensed
[jsm28/IMOLean](https://github.com/jsm28/IMOLean) project. Lazar Milikic
contributed an accepted correction to the Problem 1 move definition in
[jsm28/IMOLean#1](https://github.com/jsm28/IMOLean/pull/1).

Original source headers and license notices are preserved in the Lean modules
and accompanying `LICENSE` files. Attribution and provenance records should
remain intact when files are copied or redistributed.

The formalization work used Lean, Mathlib, public repositories, papers, and
other online documentation in addition to theorem proving. These archives are
transparent records of documented formalization work, not claims that solution
discovery was independent.

## Working with the Sources

### Exploring a declaration

Open the relevant module in VS Code with the Lean 4 extension, place the cursor
on a theorem or `theorem ...` declaration, and use Lean's hover and infoview
actions to inspect its type, local context, and proof state.

The root [`IMO2026.lean`](Solution/IMO2026.lean) file imports all six modules.
Other Lean files can be checked individually with Lake, for example:

```powershell
lake env lean IMO2026/P3.lean
```

Run this command from the appropriate `Solution/` or `Formalization/` project
directory.

### Updating dependencies

Do not change `lean-toolchain`, the mathlib revision, or `lake-manifest.json`
without understanding the effect on proof stability. For a clean dependency
refresh:

```powershell
lake update
lake exe cache get
lake build IMO2026
```

Record the resulting toolchain and manifest changes when preparing a new
reproducible release.

## Limitations and Scope

- Lean compilation verifies formal proofs, but it does not independently
  validate informal theorem statements against the original olympiad problem
  text.
- The retained verification evidence summarizes prior workflow behavior; it is not a
  replacement for mathematical review of the formalized statements.
- Raw prompts, credentials, caches, and large machine-local operational logs
  are intentionally excluded from this archive.
- The problem-by-problem status in this README describes the retained source
  files, not an independent re-solution of every theorem.

## License

The project files are distributed under the Apache License 2.0. See
[`Solution/LICENSE`](Solution/LICENSE),
[`Formalization/LICENSE`](Formalization/LICENSE), and the license headers in
the source modules.