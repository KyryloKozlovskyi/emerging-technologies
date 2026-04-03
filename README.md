# Emerging Technologies

Assessment submission for the Emerging Technologies module (Summer 25/26).

Primary deliverable: [problems.ipynb](problems.ipynb)

This notebook implements and evaluates classical and quantum approaches to the constant-vs-balanced Boolean function problem, progressing from function generation to full Deutsch-Jozsa execution in Qiskit.

Target audience: an informed computing professional who can run and evaluate the work without additional guidance.

## Quick Evaluator Path

If you are assessing this repository, the fastest path is:

1. Open [problems.ipynb](problems.ipynb).
2. Select Kernel -> Restart & Run All.
3. Confirm all test cells print pass messages.
4. Review each Problem section (1 to 5) and its Theory, Implementation, Demonstration, and Testing subsections.

Expected headline outcome:

- Classical worst-case (4-bit promise problem): $2^{n-1} + 1 = 9$ queries.
- Deutsch-Jozsa (same promise): 1 oracle query.

## Problem Coverage

The notebook addresses all five required problems from the brief.

1. Generating Random Boolean Functions:
   implement `random_constant_balanced`, which returns a randomly chosen four-input Boolean function guaranteed to be either constant or balanced.
2. Classical Testing for Function Type:
   implement `determine_constant_balanced(f)` to classify a promised oracle as `"constant"` or `"balanced"`, and analyze the maximum number of classical queries needed for certainty.
3. Quantum Oracles:
   create the four one-bit Deutsch oracles in Qiskit (for the four possible single-input Boolean functions), demonstrate their use, and explain how each circuit implements its function.
4. Deutsch's Algorithm with Qiskit:
   design and run the full Deutsch circuit using the Problem 3 oracles, and explain how interference allows one-query constant-vs-balanced classification.
5. Scaling to the Deutsch-Jozsa Algorithm:
   build a four-bit Deutsch-Jozsa circuit in Qiskit, explain the classical-to-quantum oracle encoding, and demonstrate correct classification on both constant functions and two balanced functions.

Each problem includes:

- Narrative explanation and contextualized references.
- Clean code with comments and docstrings.
- Demonstration cells.
- Dedicated verification tests.

## Assessment Alignment Notes

- Brief reference: [roughwork/assessment.md](roughwork/assessment.md)
- Guidance reference: [roughwork/notes/assessment-guidance.ipynb](roughwork/notes/assessment-guidance.ipynb)
- Referencing style in the notebook: citations are placed inline where claims are made, with context about why each source is relevant.

## Setup and Reproducibility

### Prerequisites

- [Python](https://www.python.org/downloads/) 3.10+
- [Git](https://git-scm.com/)

### Standard Local Setup

```bash
git clone https://github.com/KyryloKozlovskyi/emerging-technologies.git
cd emerging-technologies
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
jupyter notebook problems.ipynb
```

Then run all cells from a fresh kernel.

### Optional VS Code Dev Container

This repository includes a ready dev container at [.devcontainer/devcontainer.json](.devcontainer/devcontainer.json) with Python, Jupyter, and recommended extensions preconfigured.

### Reproducibility Notes

- No external datasets are required.
- No manual file downloads are required.
- The environment is defined by [requirements.txt](requirements.txt).
- Repository hygiene is controlled via [.gitignore](.gitignore).

## Evidence Against Marking Criteria

The assessment uses five equally weighted categories. Evidence in this repository is summarized below.

| Category      | Evidence in this submission                                                                                                                      |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Presentation  | Clear repository structure, concise setup instructions, logical notebook narrative, and consistent headings in [problems.ipynb](problems.ipynb). |
| Research      | Inline references in context throughout the notebook, including academic and official technical sources, with explanation of relevance.          |
| Documentation | Explanatory markdown, docstrings, targeted comments, and explicit discussion sections in each problem.                                           |
| Development   | Working implementations for all required tasks, modular functions, simulation runs, and dedicated test cells validating correctness.             |
| Consistency   | Commit history on main shows iterative problem-by-problem development, refinement, and documentation improvements over time.                     |

## Repository Structure (Required Assessment Files)

```text
emerging-technologies/
├── problems.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Submission Readiness Checklist

Before final submission, verify:

- [ ] Repository URL submitted in the required format.
- [ ] [problems.ipynb](problems.ipynb) is in the repo root and runs top-to-bottom without errors.
- [ ] [README.md](README.md), [.gitignore](.gitignore), and [requirements.txt](requirements.txt) are accurate and up to date.
- [ ] Commit history reflects steady progress and meaningful increments.
- [ ] Repository contains no unnecessary local artifacts.

## Technologies

- [Qiskit](https://www.ibm.com/quantum/qiskit)
- [Qiskit Aer](https://qiskit.github.io/qiskit-aer/)
- [Jupyter Notebook](https://jupyter.org/)
- [Python Standard Library](https://docs.python.org/3/library/) (`random`, `itertools`)
