# Paper-Level Autoformalizations

**Research-oriented mathematical formalization using Lean 4, Mathlib, and AI-assisted proof engineering.**

This repository contains machine-verified Lean 4 formalizations of mathematical research papers, International Mathematical Olympiad problems, and mathematical reasoning benchmarks.

The projects follow the [LeanFlow](https://github.com/epfl-lara/LeanFlow) workflow, combining AI-assisted proof development with formal verification by the Lean theorem prover.

The objective is to bridge the gap between informal mathematical reasoning and machine-checkable proofs.

---

## Research Highlights

- **6 IMO problems:** Formalizations of all six official IMO 2026 problems.
- **18 benchmark problems:** Formalizations covering Geometry and Combinatorics from IMO-LeanProofBench.
- **Research-paper formalizations:** Results from probability theory, mathematical statistics, number theory, and polynomial parametrization.
- **Proof verification:** Completed projects are built and checked as Lean 4 projects.
- **Reproducibility:** Each project includes its own source code, build instructions, and relevant provenance information.

## Repository Standards

The `main` branch is reserved for projects considered ready for public presentation.

Every completed project is expected to satisfy the following standards:

- Builds successfully using its specified Lake target.
- Contains no project-local `sorry` or `admit`.
- Introduces no custom `axiom`.
- Contains no `unsafe` declarations in its Lean files.
- Includes relevant source attribution and project documentation.

Work in progress is maintained separately through draft pull requests.

---

## Completed Projects

### 1. IMO 2026 — Problems 1–6

**Directory:** `IMO2026/GPT5.6`

**Mathematical Area:** Number Theory, Algebra, Combinatorics, and Geometry.

**Source:** [Official IMO 2026 Problems](https://www.imo-official.org/problems.aspx)

**Description:**

A complete Lean 4 formalization of all six problems from the 2026 International Mathematical Olympiad.

**Implementation Details:**

- Based on Joseph Myers' [IMOLean](https://github.com/jsm28/IMOLean) project.
- Developed using GPT-5.6 with high reasoning effort.
- Uses the LeanFlow workflow.
- All six formalizations are verified together as one Lean project.

**Lake Target:** `IMO2026`

---

### 2. IMO-LeanProofBench — 18 Benchmark Problems

**Directory:** `LeanIMOBench/GPT6-astra`

**Mathematical Area:** Geometry and Combinatorics.

**Source:** [Google DeepMind Superhuman Benchmark](https://github.com/google-deepmind/superhuman)

**Research Reference:** [LEAP — arXiv:2606.03303](https://arxiv.org/abs/2606.03303)

**Description:**

A collection of 18 machine-verified formalizations addressing benchmark problems for which LEAP does not publish solutions.

The collection includes:

- 12 Geometry problems.
- 6 Combinatorics problems.
- 12 problems originally composed for the benchmark and not previously published.

**Implementation Details:**

- Developed using GPT-6 Astra through the Codex provider.
- Uses an AI-assisted LeanFlow orchestration workflow.
- Every formalized statement is byte-identical to its published benchmark counterpart.
- Proof dependency graphs are documented in `DAGS.md`.
- All 18 problems are verified together as one Lean project.

**Lake Target:** `LeanIMOBench`

---

### 3. Pythagorean Polynomial Parametrization

**Directory:** `PythagoreanPolynomialParametrization`

**Mathematical Area:** Number Theory and Algebra.

**Research Paper:** [Parametrization of Pythagorean triples by a single triple of polynomials](https://arxiv.org/abs/0706.0290)

**Authors:** Sophie Frisch and Leonid Vaserstein.

**Description:**

A source-backed formalization of mathematical results concerning polynomial parametrizations of Pythagorean triples.

**Formalized Results:**

- The obstruction theorem.
- Integer-valued parametrization.
- Positive parametrization variants.
- 16-parameter variants.

**Lake Target:** `Pyth`

---

### 4. Cramer–Wold Theorem

**Directory:** `CramerWoldTheorem`

**Mathematical Area:** Probability Theory and Mathematical Statistics.

**Research Paper:** [A Calculus Proof of the Cramer-Wold Theorem](https://arxiv.org/abs/1607.03206)

**Authors:** Russell Lyons and Kevin Zumbrun.

**Description:**

A formalization of mathematical results surrounding the Cramer–Wold theorem, which establishes that a probability distribution on a finite-dimensional Euclidean space is uniquely determined by its one-dimensional projections.

**Formalized Results:**

- Half-space theorem.
- Average-distance reconstruction.
- Odd-dimensional inversion.
- Even-to-odd dimensional reduction.

**Lake Target:** `CramerWoldTheorem`

---

## Work in Progress

The following formalizations are maintained in separate draft pull requests.

| Project                                    | Research Area          |
| ------------------------------------------ | ---------------------- |
| A Short Proof of the Hilton–Milner Theorem | Extremal Combinatorics |
| Quantizing Pythagorean Triples             | Number Theory          |

These projects contain remaining proof obligations and are not presented as completed formalizations.

---

## Technology Stack

| Technology | Purpose                                        |
| ---------- | ---------------------------------------------- |
| Lean 4     | Formal theorem proving                         |
| Mathlib    | Mathematical definitions and theorem libraries |
| LeanFlow   | Formalization workflow                         |
| GPT models | AI-assisted proof development                  |
| Lake       | Lean project and dependency management         |
| Codex      | AI-assisted development environment            |

---

## Building the Projects

### Requirements

- Lean 4 toolchain specified by each project.
- Lake.
- Required Mathlib dependencies.

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

cd ../IMO2026/GPT5.6
lake build IMO2026
```

The LeanIMOBench project can also be built using its `LeanIMOBench` Lake target.

---

## Repository Structure

```text
.
├── IMO2026/
│   └── GPT5.6/
├── LeanIMOBench/
│   └── GPT6-astra/
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

Mathematical reasoning is traditionally expressed in natural language, where hidden assumptions, omitted steps, and ambiguities can be difficult to detect.

Formal verification provides a way to express mathematical arguments precisely and check their correctness mechanically.

This repository explores how modern AI systems can assist in translating mathematical research into formal proofs while retaining Lean 4 as the verification authority.

**The central principle is simple: AI can assist in constructing a proof, but the Lean kernel must verify it.**

---

## License

This repository is distributed under the [Apache License 2.0](LICENSE).

For contribution guidelines, see [CONTRIBUTING.md](CONTRIBUTING.md).

For publication notes and limitations, see [PUBLICATION_LIMITATIONS.md](PUBLICATION_LIMITATIONS.md).

For citation information, see [CITATION.cff](CITATION.cff).
