# Contribute to the Analytics Library

**Goal:** an **analysis pattern** that accepts generic data types and demonstrates the **inference** the method provides—**not** tied to a specific dataset.

> **Keep it generic:** Avoid tying the method to a single named dataset. Accept **generic data types** and show how to adapt.

!!! tip "Don’t skip interpretation"
    Every result plot should include 2–3 sentences explaining **how to read the output** and **what inference** the method supports.

## Required sections
1. **When to use** — questions the method answers; assumptions.
2. **Inputs & assumptions** — generic data shapes/types; preconditions.
3. **Step‑by‑step** (R/Python) — minimal, runnable example.
4. **Result plot + interpretation** — show output **and explain how to read it**.
5. **Settings & sensitivity** — how parameters change outcomes; defaults to start with.
6. **Pitfalls & limitations** — where it fails; what to avoid; checks to run.

## Author checklist
- [ ] Works on **generic** data types (not fixed to one dataset)
- [ ] Produces a result plot **with interpretation guidance**
- [ ] Explains parameters/settings and their effects
- [ ] Notes pitfalls/limitations and when to avoid the method
- [ ] License and links set; assets < 2 MB; alt text present

## Style guide (authoritative)
Follow the Analytics Library style rules:  
https://github.com/CU-ESIIL/analytics-library/blob/main/docs/style-guide.md

## Tiny example (placeholder)
```python
# Python
# yhat, diag = fit_and_predict(x, params)
# plt.plot(t, y, label="obs"); plt.plot(t, yhat, label="fit"); plt.legend()
```

```r
# R
# fit <- method(x, params)
# plot_result(fit)  # include a short paragraph interpreting the figure
```
