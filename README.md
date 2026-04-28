# Emerging Technologies

**Module:** Emerging Technologies, Summer 25/26  
**Author:** Kyrylo Kozlovskyi

## About This Repository

This repository contains my assessment submission for the [Emerging Technologies](https://www.atu.ie/) module at Atlantic Technological University. The work focuses on understanding and implementing the [Deutsch-Jozsa algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/deutsch-jozsa) — one of the earliest demonstrations of quantum computational advantage over classical computation.

All work is completed in a single Jupyter notebook ([`problems.ipynb`](problems.ipynb)) containing five interconnected problems that progressively build from classical Boolean function generation to a full quantum circuit implementation using [Qiskit](https://www.ibm.com/quantum/qiskit) and [Qiskit Aer](https://qiskit.github.io/qiskit-aer/).

### The Deutsch-Jozsa Problem

Given a black-box Boolean function that is promised to be either **constant** (same output for every input) or **balanced** (returns `True` for exactly half of its inputs), the goal is to determine which type it is using as few queries as possible. For a 4-bit function, a classical deterministic algorithm requires up to $2^{n-1} + 1 = 9$ queries in the worst case. The Deutsch-Jozsa quantum algorithm solves the same problem with a single query — an exponential speedup achieved through superposition and interference, as first proposed by [Deutsch (1985)](https://doi.org/10.1098/rspa.1985.0070) and generalised by [Deutsch & Jozsa (1992)](https://doi.org/10.1098/rspa.1992.0167).

## Repository Structure

```
emerging-technologies/
├── .devcontainer/          # Codespaces / devcontainer configuration
├── problems.ipynb          # Main assessment notebook (5 problems)
├── requirements.txt        # Python package dependencies
├── .gitignore              # Standard Python/Jupyter ignores
└── README.md               # This file
```

## Notebook Structure

The notebook follows a clear narrative structure, with each problem building on the previous one:

```
problems.ipynb
│
├── Title & Introduction
│   └── # Emerging Technologies
│
├── Imports
│   └── random, itertools, math, qiskit, qiskit_aer
│
├── ## Problem 1: Generating Random Boolean Functions
│   ├── Problem Description & Understanding
│   ├── Theory / Background (truth tables, binomial coefficient)
│   ├── Combinatorial verification (math.comb demo)
│   ├── Approach & Discussion
│   ├── Implementation — bin_args_to_int(), random_constant_balanced()
│   ├── Demonstration (technique demos, function calls)
│   └── Testing — test_random_constant_balanced() with statistical checks
│
├── ## Problem 2: Classical Testing for Function Type
│   ├── Problem Description & Understanding
│   ├── Theory / Background (pigeonhole principle, worst-case analysis)
│   ├── Approach & Discussion (efficiency table, probabilistic comparison)
│   ├── Implementation — determine_constant_balanced(), count_queries()
│   ├── Demonstration (10-trial demo, query distribution analysis)
│   └── Testing — test_determine_constant_balanced() + edge cases
│
├── ## Problem 3: Quantum Oracles
│   ├── Problem Description & Understanding
│   ├── Theory / Background (oracle model, gate table)
│   ├── Approach & Discussion (phase kickback, modularity)
│   ├── Implementation — make_oracle_f1() through make_oracle_f4()
│   ├── Demonstration (circuit diagrams, truth table verification)
│   ├── Reversibility check (oracle applied twice)
│   └── Testing — full_oracle_test() (4 functions × 4 states)
│
├── ## Problem 4: Deutsch's Algorithm
│   ├── Problem Description & Understanding
│   ├── Theory / Background (step-by-step derivation, interference)
│   ├── Approach & Discussion (common mistakes, determinism)
│   ├── Implementation — deutsch_algorithm()
│   ├── Demonstration (all 4 oracles, circuit diagrams)
│   ├── Classical vs quantum comparison (2× speedup table)
│   └── Testing — test_deutsch_algorithm()
│
└── ## Problem 5: Scaling to the Deutsch–Jozsa Algorithm
    ├── Problem Description & Understanding
    ├── Theory / Background (generalised derivation, oracle encoding)
    ├── Approach & Discussion (scaling argument, probabilistic comparison)
    ├── Implementation — make_dj_oracle(), deutsch_jozsa()
    ├── Demonstration (2 constant + 2 balanced, circuit diagrams)
    ├── Testing — test_deutsch_jozsa() (2 constant + 20 balanced)
    └── Summary — classical vs quantum comparison table
```

Each problem section follows a consistent pattern:

1. **Problem Description** — What the assessment requires
2. **My Understanding** — My interpretation and strategy
3. **Theory / Background** — Mathematical and quantum foundations
4. **Approach** — How I plan to implement it
5. **Discussion** — Analysis of efficiency, trade-offs, and connections
6. **Implementation** — Well-documented Python code with docstrings
7. **Demonstration** — Concrete examples and circuit diagrams
8. **Testing** — Verification with assertions and edge cases

## Problems Overview

### Problem 1: Generating Random Boolean Functions

Implements `random_constant_balanced()`, a function that randomly generates either a constant or balanced Boolean function over four inputs. Returns a **callable** `f(b1, b2, b3, b4) → bool` using closures to capture the truth table, simulating black-box oracle behaviour.

The number of balanced 4-input functions is verified as $\binom{16}{8} = 12{,}870$ using `math.comb`, and testing includes a statistical balance check (≥400 each type in 1000 trials).

### Problem 2: Classical Testing for Function Type

Implements `determine_constant_balanced(f)`, a classical algorithm that classifies a given function as constant or balanced using an early-exit strategy. The analysis establishes the worst-case query complexity of $2^{n-1} + 1 = 9$ queries for $n = 4$, forming the baseline against which the quantum algorithms are compared.

Includes an empirical query distribution analysis showing that balanced functions typically exit in ~2.8 queries on average.

### Problem 3: Quantum Oracles

Constructs quantum oracles for all four single-bit Boolean functions (`make_oracle_f1` through `make_oracle_f4`) using Qiskit. Each oracle encodes the function as a reversible unitary transformation $U_f|x\rangle|y\rangle = |x\rangle|y \oplus f(x)\rangle$.

Includes a reversibility demonstration — applying each oracle twice confirms the ancilla returns to its original state for all input combinations.

### Problem 4: Deutsch's Algorithm

Implements `deutsch_algorithm(make_oracle)` for single-bit functions. The circuit uses superposition and phase kickback to classify the function as constant or balanced using a single oracle query, compared to the two queries required classically.

Includes a classical-vs-quantum comparison table showing the 2× speedup for all four oracles.

### Problem 5: Deutsch-Jozsa Algorithm

Implements `make_dj_oracle(truth_table)` and `deutsch_jozsa(truth_table)` to handle the 4-bit functions from Problem 1. The oracle encoding uses multi-controlled X gates flanked by X gates to trigger on specific input patterns.

A closing summary table compares classical deterministic (9 queries), classical probabilistic (3 queries, 87.5% confidence), and quantum (1 query, 100% certainty) approaches, with a scaling note: for $n = 100$, classical needs up to $2^{99} + 1$ queries while Deutsch-Jozsa still needs just 1.

## Getting Started

### Option 1: GitHub Codespaces (Recommended)

The easiest way to run this notebook is with [GitHub Codespaces](https://github.com/features/codespaces), which provides a pre-configured cloud environment with no local setup required:

1. Navigate to the repository on GitHub.
2. Click the green **Code** button and select **Open with Codespaces**.
3. Once the environment loads, open `problems.ipynb`.
4. Select **Kernel > Restart & Run All** to execute every cell from scratch.

The repository includes a [devcontainer](.devcontainer/) configuration that automatically installs all dependencies, so no manual setup is needed.

### Option 2: Run Locally

#### Prerequisites

- [Python 3](https://www.python.org/downloads/) (3.10 or later recommended)
- [Git](https://git-scm.com/)

#### Clone the Repository

```bash
git clone https://github.com/KyryloKozlovskyi/emerging-technologies.git
cd emerging-technologies
```

#### Install Dependencies

It is recommended to use a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

#### Run the Notebook

```bash
jupyter notebook problems.ipynb
```

Then select **Kernel > Restart & Run All** to execute every cell from scratch and verify that the notebook runs without errors.

**Note:** Run cells in order from top to bottom, as later problems depend on functions defined in earlier ones.

## Technologies Used

| Package | Purpose |
|---|---|
| [Qiskit](https://www.ibm.com/quantum/qiskit) | Quantum circuit construction, visualisation, and simulation |
| [Qiskit Aer](https://qiskit.github.io/qiskit-aer/) | Local quantum simulator backend (`qasm_simulator`) |
| [`random`](https://docs.python.org/3/library/random.html) | Generating constant and balanced truth tables |
| [`itertools`](https://docs.python.org/3/library/itertools.html) | Producing all Boolean input combinations |
| [`math`](https://docs.python.org/3/library/math.html) | Binomial coefficient verification (`math.comb`) |

## Key Concepts Demonstrated

### Phase Kickback

When the ancilla qubit is prepared in $|-\rangle$, the oracle's effect simplifies from a bit flip to a phase: $U_f|x\rangle|-\rangle = (-1)^{f(x)}|x\rangle|-\rangle$. This is the mechanism that enables the quantum speedup.

### Constructive and Destructive Interference

For constant functions, all phase terms are identical and add constructively — the probability of measuring all zeros is 1. For balanced functions, half the terms are $+1$ and half are $-1$, producing perfect destructive interference — the probability of measuring all zeros is 0.

### Oracle Reversibility

Since XOR is its own inverse ($y \oplus f(x) \oplus f(x) = y$), applying any oracle twice restores the original state. This is verified experimentally for all oracles in Problem 3.

### Exponential Quantum Speedup

The classical worst case grows as $O(2^n)$ while the quantum algorithm always uses exactly 1 query. For $n = 100$, this means $2^{99} + 1$ classical queries versus 1 quantum query.

## Testing

Each problem includes a dedicated test function with assertions verified against known correct outputs:

| Test Function | What It Verifies |
|---|---|
| `test_random_constant_balanced()` | 1000 trials: callable, correct type, statistical balance (≥400 each) |
| `test_determine_constant_balanced()` | 1000 trials: correct classification, constant always uses 9 queries |
| `full_oracle_test()` | 4 functions × 4 input states = 16 tests against expected truth tables |
| `test_deutsch_algorithm()` | All 4 oracles classified correctly, all results deterministic |
| `test_deutsch_jozsa()` | 2 constant (deterministic `0000`) + 20 random balanced (`0000` never appears) |

## References

The notebook draws on the following key academic sources, cited inline throughout:

- Deutsch, D. (1985). *Quantum theory, the Church-Turing principle and the universal quantum computer.* Proceedings of the Royal Society A. [doi:10.1098/rspa.1985.0070](https://doi.org/10.1098/rspa.1985.0070)
- Deutsch, D. & Jozsa, R. (1992). *Rapid solution of problems by quantum computation.* Proceedings of the Royal Society A. [doi:10.1098/rspa.1992.0167](https://doi.org/10.1098/rspa.1992.0167)
- de Wolf, R. (2019). *Quantum Computing: Lecture Notes.* [arXiv:1907.09415](https://arxiv.org/abs/1907.09415)
- Aaronson, S. *Quantum Computing Since Democritus*, [Lecture 17](https://www.scottaaronson.com/qclec/17.pdf).
- [IBM Quantum Learning](https://quantum.cloud.ibm.com/learning) — course materials on quantum circuits, single systems, and the Deutsch-Jozsa algorithm.

---

AI assistance tools (GitHub Copilot, Claude Sonnet 4.6, Claude Opus 4.6, Claude Opus 4.7) were used to help generate test cases, draft docstrings, and write code comments.