# CDMO Project: Sports Tournament Scheduling (STS)

This repository contains our solution for the **Combinatorial Decision Making and Optimization (CDMO)** course project at the University of Bologna for the academic year 2024/2025. The project focuses on modelling and solving the **Sports Tournament Scheduling (STS)** problem using three different technologies: a two-phase Constraint Programming (CP) approach, a propositional SATisfiability (SAT) solver, and a Mixed-Integer Linear Programming (MIP) model.

## Technologies & Approaches

1.  **Constraint Programming (CP):**
    *   **`simple_CP.mzn`**: A basic MiniZinc model to find a feasible schedule.
    *   **`phase2_optimize.mzn`**: An optimization model that takes a feasible solution and minimizes home/away imbalance by swapping assignments.
    *   **`run_2phaseCP_solver.py`**: A Python script that orchestrates the two-phase process (feasibility then optimization) using the `minizinc` Python package and the Gecode solver.
    *   **`runCP_solvers.py`**: A script to run individual CP models.(without optimization)

2.  **Propositional SATisfiability (SAT):**
    *   **`z3_SAT.py`**: A Python script that encodes the STS problem into a propositional SAT formula using the Z3 API, solves it, and outputs the results.

3.  **Mixed-Integer Linear Programming (MIP):**
    *   **`MIP.py`**: A Python script that formulates the STS problem as a MIP model using a library like PuLP or CVXPY, solves it using a solver like CBC or Gurobi, and outputs the results.

## Prerequisites

*   Python 3.8+
*   Required Python packages (install via `pip install -r requirements.txt`):
    *   `minizinc` (for CP models)
    *   `z3-solver` (for SAT model)
    *   `pulp` or `cvxpy` (for MIP model)
*   The MiniZinc language and the Gecode solver must be installed on your system. Please follow the instructions on [https://www.minizinc.org/](https://www.minizinc.org/) to set it up. The `minizinc` Python package requires the MiniZinc binary to be in your system's PATH.

## Usage

The scripts are designed to be executed independently. Each will generate the required `.json` result files in the `res/` directory.

**1. Run the Two-Phase CP Solver:**
```bash
# This runs the simple_CP model for feasibility, then phase2_optimize for H/A balance.
python source/CP/run_2phaseCP_solver.py
python source/SAT/z3_SAT.py
python source/MIP/MIP.py
