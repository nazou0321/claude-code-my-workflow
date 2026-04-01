---
paths:
  - "Labs/**/*.do"
---

# STATA Do-file Conventions

**Every STATA do-file in `Labs/` must follow these conventions.**

---

## File Naming

```
Lab_D[N][A/B]_[Topic].do
```

Examples:
- `Lab_D1B_Settele2022.do`
- `Lab_D2B_Braghieri2022.do`
- `Lab_D3B_Aghion2013.do`

---

## Standard Header Block

Every do-file begins with:

```stata
// ============================================================
// Project:   MN52233 — Causal Identification Strategies
// Session:   Day [N], Session [A/B]
// Topic:     [Topic description]
// Replication: [Author(s) (Year), Journal]
// Author:    [Your name]
// Date:      [YYYY-MM-DD]
// ============================================================

clear all
set more off
capture log close
log using "logs/Lab_D[N][X]_[Topic].log", replace

global projectdir "../../"   // adjust depth as needed — never hardcode absolute paths
```

---

## Path Convention

- **Always relative.** Use `$projectdir` global set at the top.
- **Never** `/Users/...` or `C:\Users\...` paths.
- Data goes in `$projectdir/data/` or a subfolder named after the replication paper.

---

## Seed Convention

Set the seed **once**, immediately before any stochastic command:

```stata
set seed 12345
bootstrap, reps(500): regress y x
```

---

## Section Dividers

Divide the do-file into clearly labeled sections:

```stata
// ===== 0. SETUP & DATA LOADING =====
// ===== 1. DESCRIPTIVE STATISTICS =====
// ===== 2. MAIN ESTIMATION =====
// ===== 3. ROBUSTNESS CHECKS =====
// ===== 4. FIGURES =====
// ===== 5. TABLES =====
```

---

## Output: Tables

All tables must be **saved to disk** (never screen-only):

```stata
// Preferred: estout / esttab
esttab model1 model2 using "output/tables/Table1.tex", replace ///
    booktabs label se star(* 0.10 ** 0.05 *** 0.01)

// Alternative: outreg2
outreg2 using "output/tables/Table1.doc", replace
```

---

## Output: Figures (Okabe-Ito palette — mandatory)

All figures must use the Okabe-Ito colorblind-safe palette and be exported to disk:

```stata
// Okabe-Ito colors (define at top of figures section)
local c1 "0 114 178"    // Blue     #0072B2
local c2 "230 159 0"    // Orange   #E69F00
local c3 "0 158 115"    // Green    #009E73
local c4 "86 180 233"   // Sky      #56B4E9
local c5 "213 94 0"     // Vermillion #D55E00
local c6 "204 121 167"  // Pink     #CC79A7
local c7 "240 228 66"   // Yellow   #F0E442

// Export
graph export "output/figures/Fig1_[name].pdf", replace
```

**Never use default Stata colors in output figures.** No red/green combinations.

---

## Closing

Every do-file ends with:

```stata
log close
```

---

## Quality Checklist (before committing)

- [ ] Do-file runs end-to-end without errors (`do Lab_D[N][X]_[Topic].do`)
- [ ] No absolute paths anywhere
- [ ] `set seed` present before any stochastic command
- [ ] `log using` at top, `log close` at bottom
- [ ] All tables saved to `output/tables/`
- [ ] All figures saved to `output/figures/` using Okabe-Ito colors
- [ ] Estimator in code matches estimator described on corresponding slides
