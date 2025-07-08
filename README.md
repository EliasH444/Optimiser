# Hydrostatic Thrust Bearing Optimisation

## Overview

The aim of the assignment was to minimise the **power loss** in a hydrostatic thrust bearing by applying two optimisation algorithms:

- **Random Search (RS)**
- **Simulated Annealing (SA)**

Both algorithms were implemented from scratch in Python without using black-box solvers. The objective and constraint functions are based on a mathematical model of hydrostatic bearing performance.

---

## Problem Description

The optimisation problem is defined as:

**Minimise:**


**Subject to 7 constraints:**

- g₁(x) = 101000 − W(x) ≤ 0
- g₂(x) = P₀(x) − 1000 ≤ 0
- g₃(x) = ΔT(x) − 50 ≤ 0
- g₄(x) = 0.001 − h(x) ≤ 0
- g₅(x) = x₂ − x₃ ≤ 0
- g₆(x) = (0.0307 * x₁) / (772.8 * π * P₀(x) * h(x) * x₃) − 0.001 ≤ 0
- g₇(x) = W(x) / (π * (x₃² − x₂²)) − 5000 ≤ 0

**Design variables:**
- x₁: Flow rate (Q)
- x₂: Recess radius (R₀)
- x₃: Step radius (R)
- x₄: Fluid viscosity (µ)

**Bounds:**  
Each variable ∈ [1, 16]

---

## File Structure

- `notebook.ipynb`: The Jupyter notebook containing full implementation and results.
- `README.md`: You’re reading it!
- `CW1_2023_24_v1.3.pdf`: Coursework brief (provided by instructor).

---

## Key Features

- **Objective Function + Constraints:**  
  All functions `f(x)` and `g1(x)` to `g7(x)` are implemented independently with function call counters to track evaluations.

- **Constraint Handling:**  
  A **penalty-based approach** is used to penalise infeasible solutions during the optimisation process.

- **Random Search:**  
  Uniform sampling within the design space followed by penalty handling for constraint violation.

- **Simulated Annealing:**  
  Gaussian perturbations around the current solution with probabilistic acceptance of worse solutions, promoting exploration.

- **Repeatability:**  
  Results are generated using fixed random seeds to ensure consistency across runs.

- **Performance Comparison:**  
  21 runs of each optimiser are performed and compared using a boxplot to evaluate their effectiveness and robustness.

---

## Example Output

- Lowest value found (SA): ~19,213
- SA shows smaller variance and consistently better solutions than Random Search.

![Boxplot](your_boxplot_image_path.png)

---

## Getting Started

### Requirements

- Python 3.x
- Numpy
- Scipy
- Matplotlib
- Jupyter Notebook

### Running the Code

```bash
git clone https://github.com/yourusername/hydrostatic-bearing-optimisation.git
cd hydrostatic-bearing-optimisation
jupyter notebook
