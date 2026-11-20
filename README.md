# Paper-Level Autoformalizations

**Independent Mathematical Formalization | Lean 4 | Formal Verification | Research Mathematics**

A collection of mathematical research formalizations developed through independent mathematical reasoning and implemented in Lean 4 using Mathlib.

This repository focuses on translating mathematical arguments from research papers, olympiad problems, and mathematical benchmarks into precise, machine-verifiable formal proofs.

The central objective is to bridge the gap between conventional mathematical proofs and computer-verified mathematics.

All completed projects are maintained on the `main` branch and are intended to meet strict formal verification standards.

---

## Research Highlights

- **IMO 2026:** Formalization of all six International Mathematical Olympiad problems.
- **IMO-LeanProofBench:** Eighteen formalized benchmark problems covering Geometry and Combinatorics.
- **Number Theory:** Polynomial parametrization of Pythagorean triples.
- **Probability Theory:** Formalization of the Cramer–Wold theorem and related results.
- **Formal Verification:** Completed projects build successfully and contain no project-local `sorry`, `admit`, custom `axiom`, or `unsafe` declarations.

---

## Completed Research Projects

### 1. IMO 2026 — Problems 1–6

**Directory:** `IMO2026/Solution`

**Area:** Mathematical Olympiad, Number Theory, Algebra, Geometry, and Combinatorics.

**Source:** [Official IMO 2026 Problems](https://www.imo-official.org/problems.aspx)

A complete Lean 4 formalization of all six problems from the 2026 International Mathematical Olympiad.

The project focuses on translating olympiad-level mathematical arguments into formal proof structures, including supporting lemmas and intermediate results.

**Lake Target:** `IMO2026`

---

### 2. IMO-LeanProofBench — 18 Problems

**Directory:** `LeanIMOBench/Solution`

**Area:** Geometry and Combinatorics.

**Source:** [Google DeepMind Superhuman Benchmark](https://github.com/google-deepmind/superhuman)

**Research Reference:** [LEAP — arXiv:2606.03303](https://arxiv.org/abs/2606.03303)

A collection of eighteen formalized benchmark problems:

- 12 Geometry problems.
- 6 Combinatorics problems.
- 12 problems originally composed for the benchmark and never previously published.

Every formalized statement is byte-identical to its published benchmark counterpart.

Proof dependency graphs are documented in the project evidence and source files.

**Lake Target:** `LeanIMOBench`

---

### 3. Pythagorean Polynomial Parametrization

**Directory:** `PythagoreanPolynomialParametrization`

**Area:** Number Theory and Algebra.

**Research Paper:** [Parametrization of Pythagorean triples by a single triple of polynomials](https://arxiv.org/abs/0706.0290)

**Authors:** Sophie Frisch and Leonid Vaserstein.

A source-backed formalization of results concerning polynomial parametrizations of Pythagorean triples.

**Formalized Results:**

- Obstruction theorem.
- Integer-valued parametrization.
- Positive parametrization variants.
- 16-parameter variants.

**Lake Target:** `Pyth`

---

### 4. Cramer–Wold Theorem

**Directory:** `CramerWoldTheorem`

**Area:** Probability Theory and Mathematical Statistics.

**Research Paper:** [A Calculus Proof of the Cramer-Wold Theorem](https://arxiv.org/abs/1607.03206)

**Authors:** Russell Lyons and Kevin Zumbrun.

A formalization of mathematical results surrounding the Cramer–Wold theorem, which establishes that probability distributions on finite-dimensional Euclidean spaces are uniquely determined by their one-dimensional projections.

**Formalized Results:**

- Half-space theorem.
- Average-distance reconstruction.
- Odd-dimensional inversion.
- Even-to-odd dimensional reduction.

**Lake Target:** `CramerWoldTheorem`

---

## Work in Progress

The following projects are maintained separately as draft pull requests.

| Project                                    | Mathematical Area      |
| ------------------------------------------ | ---------------------- |
| A Short Proof of the Hilton–Milner Theorem | Extremal Combinatorics |
| Quantizing Pythagorean Triples             | Number Theory          |

These projects contain remaining proof obligations and are not represented as completed formalizations.

---

## Mathematical and Technical Skills

- Mathematical logic and formal proof construction.
- Number theory and polynomial parametrization.
- Probability theory and mathematical statistics.
- Geometry and combinatorics.
- Lean 4 theorem proving.
- Mathlib theorem and definition reuse.
- Proof decomposition and dependency analysis.
- Formal verification and debugging.

---

## Technology Stack

| Technology | Purpose                            |
| ---------- | ---------------------------------- |
| Lean 4     | Formal theorem proving             |
| Mathlib    | Mathematical library               |
| Lake       | Project management and compilation |

---

## Verification and Reproducibility

The repository follows a strict publication standard.

Every completed project is expected to:

1. Compile successfully using its specified Lake target.
2. Contain no project-local `sorry` or `admit`.
3. Introduce no custom axioms.
4. Avoid `unsafe` declarations in its Lean files.
5. Include relevant mathematical source attribution.

### Build All Completed Projects

```bash
./scripts/check-projects.sh
```

### Build Individual Projects

```bash
cd PythagoreanPolynomialParametrization
lake build Pyth

cd ../CramerWoldTheorem
lake build CramerWoldTheorem

cd ../IMO2026/Solution
lake build IMO2026
```

---

## Repository Structure

```text
.
├── IMO2026/
│   └── Solution/
├── LeanIMOBench/
│   └── Solution/
├── PythagoreanPolynomialParametrization/
├── CramerWoldTheorem/
├── scripts/
│   └── check-projects.sh
├── CONTRIBUTING.md
├── PUBLICATION_LIMITATIONS.md
├── CITATION.cff
└── README.md
```

---

## Research Philosophy

Formal mathematics requires more than producing a convincing mathematical argument. Each definition, assumption, intermediate result, and proof step must be expressed precisely enough for machine verification.

This repository explores the formalization of challenging mathematical results through Lean 4, with an emphasis on correctness, reproducibility, and mathematical transparency.

**The ultimate standard is not whether a proof looks correct, but whether it can be verified by the Lean kernel.**

---

## License and Contributions

Licensed under the [Apache License 2.0](LICENSE).

- [Contribution Guidelines](CONTRIBUTING.md)
- [Publication Limitations](PUBLICATION_LIMITATIONS.md)
- [Citation Metadata](CITATION.cff)
