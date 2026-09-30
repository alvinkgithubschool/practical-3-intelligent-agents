# Practical 3 — Intelligent Agents: Policy Iteration & Value Iteration

**Strathmore University — School of Computing and Engineering Sciences (SCES)**

Implementation and analysis of the two classical dynamic-programming algorithms for solving
Markov Decision Processes (MDPs) on a stochastic 6x6 gridworld.

## Structure

```
├── Practical_3_Policy_and_Value_Iteration_Report.ipynb   # Main deliverable: implementation + analysis + report
├── Codes (1)/                    # Provided source code (unmodified)
│   ├── main.py                   # Interactive launcher (pygame UI) — run locally, not in Colab
│   ├── environment.py           # Gridworld MDP (states, actions, transition model, rewards)
│   ├── constants.py              # Grid layout, rewards, discount factor, stopping error
│   ├── complex_constants.py      # Alternative 18x18 random-grid variant
│   ├── algorithms/
│   │   ├── value_iteration.py    # Value Iteration solver
│   │   └── policy_iteration.py  # Policy Iteration solver
│   ├── data_recorder.py          # Writes per-cell utilities across iterations to CSV
│   ├── interface.py              # pygame display (desktop only)
│   ├── data_analysis/            # Provided analysis notebooks
│   └── recorded_data/            # CSVs recorded from the 18x18 variant
├── updated_value_iteration_analysis.ipynb   # Provided analysis notebook (value iteration)
├── updated_policy_iteration_analysis.ipynb  # Provided analysis notebook (policy iteration)
└── ARCHIVE_README.md             # Original course README (course overview and syllabus)
```

## Output

All results are **embedded in the report notebook**
(`Practical_3_Policy_and_Value_Iteration_Report.ipynb`): the converged utilities, the optimal
policies, the convergence figures, the algorithm-comparison tables, and the full written report.
The notebook has already been executed on Google Colab, so every output is visible without
re-running it. Re-running it additionally writes the per-iteration utility data to
`recorded_data/value_iteration.csv` and `recorded_data/policy_iteration.csv`.

## How to run

- **Report notebook (Colab):** open the notebook at [colab.research.google.com](https://colab.research.google.com)
  via *File → Upload notebook*, then *Runtime → Run all*. No installs needed — it only uses
  `numpy`, `pandas` and `matplotlib`, all pre-installed in Colab.
- **Original pygame program (local machine only):** `pip install -r "Codes (1)/requirements.txt"`,
  then `python main.py` from inside `Codes (1)` and choose Value Iteration or Policy Iteration.

## Key findings

- Both algorithms converge to the **identical optimal policy** in all 31 reachable cells.
- Value Iteration: 757 grid sweeps; Policy Iteration: 7 improvement rounds (700 evaluation
  sweeps), roughly 3x faster wall-clock since evaluation checks 1 action per cell instead of 4.
- Utilities lie between 88.5 and ~100 (the `R_max/(1-gamma)` ceiling) because the task has no
  terminal states; gamma = 0.99 dominates the values.
- Policy Iteration needs at least 10 evaluation sweeps per round here; 5 sweeps yields a
  sub-optimal policy.

See Section 10 of the report notebook for the full discussion.
