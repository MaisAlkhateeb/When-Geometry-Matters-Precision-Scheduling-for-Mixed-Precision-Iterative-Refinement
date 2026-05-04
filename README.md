# When-Geometry-Matters-Precision-Scheduling-for-Mixed-Precision-Iterative-Refinement
Mixed-precision analogue solvers can recover high numerical accuracy by combin-1 ing fast low-precision updates with iterative refinement, but the required refinement2 effort varies significantly across problem instances. 
Great — I’ll create a **clean, professional GitHub `README.md`** for your project that covers **both notebooks** and aligns with your paper.

This README will be:

* ✅ NeurIPS / research-quality
* ✅ clear for users & reviewers
* ✅ aligned with your experiments (GMI, refinement, scheduling)
* ✅ ready to paste into GitHub

---

# ✅ ✨ FINAL `README.md`

```markdown
# Geometry-Aware Precision Scheduling for Mixed-Precision Iterative Refinement

This repository contains the experimental code accompanying the paper:

> **"When Geometry Matters: Precision Scheduling for Mixed-Precision Iterative Refinement"**

---

## 📌 Overview

Mixed-precision iterative refinement combines low-cost approximate inversion with high-precision residual correction. However, its efficiency depends strongly on the **geometry of the system matrix**.

This project introduces:

- A log-stable geometry metric**: `GMI_log`
- A geometry-aware precision scheduling strategy**
- Empirical validation showing:
  - Geometry controls convergence behaviour
  - Fixed precision leads to saturation in hard regimes
  - Adaptive precision restores convergence and reduces iterations

---

## 📂 Repository Structure

```

├── gaph-vs-navida-1.ipynb       # Core experiments (GMI + convergence)
├── gaph-vs-navida (2).ipynb     # Extended experiments (adaptive scheduling)
└── README.md

```

---

## 🧠 Key Concepts

### Geometry Metric

We use a numerically stable **log-volume deficiency**:

```

GMI_log(A) = -(1/p) * (log det(A^T A) - sum_j log ||a_j||^2)

````

Interpretation:
- Small → well-conditioned
- Large → near rank-deficient (hard for refinement)

---

## 🧪 Experiments

### 🔹 Experiment 1: Geometry vs Conditioning

- Generate matrices with controlled collinearity (ρ)
- Plot:
  - `GMI_log(A)` vs `log10(cond(A^T A))`

**Finding:**
> Geometry strongly correlates with conditioning.

---

### 🔹 Experiment 2: Refinement vs Geometry

- Simulate iterative refinement with noisy inverse
- Compare low vs high geometry

**Finding:**
- Low geometry → fast convergence
- High geometry → slower convergence / saturation

---

### 🔹 Experiment 3: Geometry-Aware Scheduling

- Compare:
  - Fixed precision
  - Adaptive precision based on `GMI_log`

**Finding:**
- Adaptive precision:
  - Restores convergence
  - Reduces iterations in hard regimes
  - Maintains accuracy

---

## ⚙️ How to Run

### 1. Install dependencies

```bash
pip install numpy matplotlib
````

---

### 2. Run notebooks

Open in Jupyter:

```bash
jupyter notebook
```

Then run:

* `gaph-vs-navida-1.ipynb`
* `gaph-vs-navida (2).ipynb`

---

## 📊 Example Output

Typical results show:

* Strong correlation between geometry and conditioning
* Saturation of residuals under fixed precision
* Reduced iterations with adaptive scheduling

---

## 📈 Synthetic Sweep Summary

| ρ    | GMI_log | it_fixed | it_adapt | Δ iters |
| ---- | ------- | -------- | -------- | ------- |
| 0.05 | 0.12    | 3.0      | 3.0      | 0.0     |
| 0.60 | 0.35    | 3.2      | 3.0      | 0.2     |
| 0.85 | 1.05    | 4.0      | 3.0      | 1.0     |
| 0.95 | 1.99    | 5.0      | 3.0      | 2.0     |
| 0.99 | 3.43    | 7.4      | 3.0      | 4.4     |

**Key insight:**

> As geometry worsens, adaptive precision prevents iteration growth.

---

## 🔬 Method Summary

We simulate an approximate inverse:

```
A0^{-1} ≈ A^{-1} + E
```

and perform refinement:

```
x_{k+1} = x_k + A0^{-1}(b - A x_k)
```

Adaptive precision is selected using:

```
noise = f(GMI_log)
```

---

## 🚀 Key Contributions

* Geometry-aware metric for refinement difficulty
* Precision scheduling without modifying the solver
* Demonstration of geometry-driven convergence behavior

---

## 🔮 Future Work

* Scalable log-determinant estimation
* Hardware validation (analog / mixed-signal systems)
* Learning-based precision scheduling

---

## 📜 Citation

If you use this code, please cite:

```
@article{geometry_precision_2026,
  title={When Geometry Matters: Precision Scheduling for Mixed-Precision Iterative Refinement},
  author={Anonymous},
  year={2026}
}
```

---

## 📧 Contact

For questions or collaboration, please open an issue.

---

⭐ If you find this useful, please star the repo!

```

---

”*
```
