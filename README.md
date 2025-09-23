# Prisoner Riddle

## 🔐 100 Prisoners Problem — Simulation & Visualization

## Overview

This project explores the **100 Prisoners Problem**, a classic probability riddle that at first glance appears unwinnable — yet has a surprisingly elegant solution rooted in permutation cycles.

We implement, simulate, and visualize two competing strategies:

1. **Random-Draw Strategy** – each prisoner opens 50 random drawers.
2. **Cycle-Following Strategy** – each prisoner follows the cycle in the permutation starting from their own drawer.

By running large-scale Monte Carlo simulations, we estimate survival probabilities, study cycle length distributions, and visualize cycle structures both statically (with NetworkX + Matplotlib) and interactively (with Plotly / PyVis).

---

## Problem Statement

* **Setup:**

  * 100 prisoners are numbered 1–100.
  * 100 drawers each contain one prisoner’s number, shuffled randomly.

* **Rules:**

  * Each prisoner may open **50 drawers** to find their number.
  * Drawers are closed after each attempt.
  * Prisoners cannot communicate after the game starts.
  * If *any* prisoner fails, **all are executed**.

* **Goal:**

  * Maximize the probability that *all 100 prisoners succeed*.

* **Naïve intuition:** \~\$(1/2)^{100}\$ survival probability (≈ zero).

* **Cycle-following strategy:** raises survival probability to **≈ 31%**.

---

## Features

✔️ Monte Carlo simulation of both strategies (default 20,000 trials)
✔️ Statistical analysis with survival probabilities + standard errors
✔️ Visualization outputs:

* **Bar chart** comparing survival probabilities
* **Histogram** of maximum cycle lengths across permutations
* **Cycle visualizations:**

  * Static plots (NetworkX + Matplotlib)
  * Interactive plots (Plotly, PyVis) with zoom, pan, hover
    ✔️ Reproducible with fixed seeds
    ✔️ Exports results to CSV and figures for further use

---

## Installation

Clone the repository:

```bash
git clone https://github.com/Kam-Willy/100PrisonersRiddle.git
cd 100PrisonersRiddle
```

Install dependencies:

**Requirements:**

* Python 3.8+
* numpy
* pandas
* matplotlib
* seaborn
* networkx
* plotly

---

## Usage

### Run Simulation

You can run the full simulation from the command line:
---

### Key Parameters

Inside `100PrisonerRiddle.ipynb` you can adjust:

```python
N_PRISONERS = 100       # number of prisoners
MAX_OPENS = 50          # drawers allowed to open
TRIALS = 20000          # Monte Carlo trials
```

---

## Outputs

### 1. 📊 Bar Chart – Survival Probabilities

Compares **Cycle-Following** vs **Random-Draw** success rates.

### 2. 📈 Histogram – Cycle Lengths

Shows distribution of maximum cycle lengths across random permutations, with threshold line at `MAX_OPENS`.

### 3. 🔄 Graph Visualizations of Cycles

* **Static:** Matplotlib circular layouts of full permutation.
* **Interactive:**

  * **Plotly** – zoom, pan, hover tooltips inside Jupyter.

### 4. 📂 Results Export

## Example Results (n=100, opens=50)

| Strategy        | Probability | Std. Error |
| --------------- | ----------- | ---------- |
| Cycle-Following | \~0.3118    | ±0.003     |
| Random-Draw     | ≈ 1e-30     | negligible |

**Key insight:** The cycle-following strategy leverages the structure of permutations — success is guaranteed as long as no cycle exceeds 50 in length. This structural property is why the survival chance is surprisingly high.

---

## Extensions

* ✅ Generalize to *n prisoners* and *k drawer opens*
* ✅ Study cycle length distributions across different n
* ✅ Explore analytical proofs (via permutation cycle theory)
* ✅ Interactive dashboards (Streamlit/Voila) for educational demos

---

## References

* Original riddle description: [100 Prisoners Problem – Wikipedia](https://en.wikipedia.org/wiki/100_prisoners_problem)
* Probabilistic analysis: Random permutation cycle decomposition theory
* Visual inspiration: NetworkX + Plotly for permutation graphs

---

## License

This project is licensed under the Apache 2.0 License.

---
