# Emerging Technologies

**Module:** Emerging Technologies, Summer 25/26  
**Author:** Kyrylo Kozlovskyi

## About This Repository

This repository contains my assessment submission for the [Emerging Technologies](https://www.atu.ie/) module at Atlantic Technological University. The primary deliverable is a Jupyter notebook ([`problems.ipynb`](problems.ipynb)) that explores the difference between classical and quantum approaches to determining whether a Boolean function is constant or balanced.

The notebook focuses on the [Deutsch-Jozsa algorithm](https://quantum.cloud.ibm.com/learning/en/modules/computer-science/deutsch-jozsa) — one of the earliest demonstrations of quantum computational advantage. First proposed by [Deutsch (1985)](https://doi.org/10.1098/rspa.1985.0070) for the single-bit case and later generalised by [Deutsch & Jozsa (1992)](https://doi.org/10.1098/rspa.1992.0167), the algorithm determines a global property of a function using a single quantum query where a classical approach may require up to nine.

All quantum circuits are implemented using [Qiskit](https://www.ibm.com/quantum/qiskit) and simulated locally with [Qiskit Aer](https://qiskit.github.io/qiskit-aer/).

## Notebook Overview

The notebook works through five problems that build on each other, progressing from classical computation to quantum circuit design:

1. **Generating Random Boolean Functions** — constructing callable oracle functions that are either constant or balanced, using truth tables and closures to simulate black-box behaviour.
2. **Classical Testing for Function Type** — building a deterministic classifier with an early-exit strategy, and analysing its worst-case query complexity ($2^{n-1} + 1 = 9$ queries for $n = 4$) using the pigeonhole principle.
3. **Quantum Oracles** — encoding the four single-bit Boolean functions as reversible quantum gate circuits using X and CX gates, following the standard oracle model $U_f|x\rangle|y\rangle = |x\rangle|y \oplus f(x)\rangle$.
4. **Deutsch's Algorithm** — implementing the single-bit quantum algorithm with Qiskit, demonstrating phase kickback and interference to classify an oracle with one query.
5. **Deutsch-Jozsa Algorithm** — generalising to 4-bit inputs using multi-controlled X gates, showing that a single quantum query replaces up to nine classical queries.

Each problem includes a structured narrative (Problem Description, My Understanding, Theory/Background, Approach, Discussion, Implementation, Demonstration, and Testing), code implementations with comments and docstrings, circuit diagrams, and independent verification tests.

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

Then select **Kernel > Restart & Run All** to execute every cell from scratch and verify that the notebook runs without errors.

## Repository Structure

```
emerging-technologies/
├── problems.ipynb      # Main assessment notebook (5 problems)
├── requirements.txt    # Python package dependencies
├── .gitignore          # Standard Python/Jupyter ignores
└── README.md           # This file
```

## Technologies Used

- [Qiskit](https://www.ibm.com/quantum/qiskit) — quantum circuit construction, visualisation, and simulation. Used to build the oracle circuits, Deutsch's algorithm circuit, and the Deutsch-Jozsa circuit.
- [Qiskit Aer](https://qiskit.github.io/qiskit-aer/) — local quantum simulator backend (`qasm_simulator`) for executing circuits without access to real quantum hardware.
- [Python Standard Library](https://docs.python.org/3/library/) — `random` for generating constant and balanced truth tables, `itertools` for producing all Boolean input combinations.

## References

The notebook draws on the following key academic sources, cited inline throughout:

- Deutsch, D. (1985). *Quantum theory, the Church-Turing principle and the universal quantum computer.* Proceedings of the Royal Society A. [doi:10.1098/rspa.1985.0070](https://doi.org/10.1098/rspa.1985.0070)
- Deutsch, D. & Jozsa, R. (1992). *Rapid solution of problems by quantum computation.* Proceedings of the Royal Society A. [doi:10.1098/rspa.1992.0167](https://doi.org/10.1098/rspa.1992.0167)
- de Wolf, R. (2019). *Quantum Computing: Lecture Notes.* [arXiv:1907.09415](https://arxiv.org/abs/1907.09415)
- Aaronson, S. *Quantum Computing Since Democritus*, [Lecture 17](https://www.scottaaronson.com/qclec/17.pdf).
- [IBM Quantum Learning](https://quantum.cloud.ibm.com/learning) — course materials on quantum circuits, single systems, and the Deutsch-Jozsa algorithm.
