# Emerging Technologies

**Module:** Emerging Technologies, Summer 25/26

## About This Repository

This repository contains my assessment submission for the Emerging Technologies module. The primary deliverable is a Jupyter notebook ([`problems.ipynb`](problems.ipynb)) that explores the [Deutsch–Jozsa algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/deutsch-jozsa) — one of the earliest demonstrations of quantum computational advantage over classical computation.

The notebook progresses from classical Boolean function generation through to quantum circuit design using [Qiskit](https://www.ibm.com/quantum/qiskit), showing how a quantum computer can determine a global property of a function with a single query where a classical computer may need up to nine.

## Notebook Overview

The notebook works through five problems that build on each other:

1. **Generating Random Boolean Functions** — constructing callable oracle functions that are either constant or balanced, using truth tables and closures.
2. **Classical Testing for Function Type** — building a deterministic classifier with an early-exit strategy, and analysing its worst-case query complexity ($2^{n-1} + 1 = 9$ queries for $n = 4$).
3. **Quantum Oracles** — encoding the four single-bit Boolean functions as reversible quantum gate circuits using X and CX gates.
4. **Deutsch's Algorithm** — implementing the single-bit quantum algorithm with Qiskit, demonstrating phase kickback and interference to classify an oracle with one query.
5. **Deutsch–Jozsa Algorithm** — generalising to 4-bit inputs using multi-controlled X gates, showing that a single quantum query replaces up to nine classical queries.

Each problem includes a narrative explanation with mathematical background, a code implementation with comments and docstrings, demonstrations with circuit diagrams, and independent verification tests.

## Getting Started

### Prerequisites

- [Python 3](https://www.python.org/downloads/) (3.10 or later recommended)
- [Git](https://git-scm.com/)

### Clone the Repository

```bash
git clone https://github.com/KyryloKozlovskyi/emerging-technologies.git
cd emerging-technologies
```

### Install Dependencies

It is recommended to use a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### Run the Notebook

```bash
jupyter notebook problems.ipynb
```

Then select **Kernel → Restart & Run All** to execute every cell from scratch.

## Repository Structure

```
emerging-technologies/
├── problems.ipynb      # Main assessment notebook
├── requirements.txt    # Python dependencies
├── .gitignore          # Standard Python/Jupyter ignores
└── README.md           # This file
```

## Technologies Used

- [Qiskit](https://www.ibm.com/quantum/qiskit) — quantum circuit construction, visualisation, and simulation. Used to implement the oracle circuits, Deutsch's algorithm, and the Deutsch–Jozsa algorithm.
- [Qiskit Aer](https://qiskit.github.io/qiskit-aer/) — local quantum simulator backend (`qasm_simulator`) for running circuits without access to real quantum hardware.
- [Python Standard Library](https://docs.python.org/3/library/) — `random` for oracle generation, `itertools` for input combinations.
