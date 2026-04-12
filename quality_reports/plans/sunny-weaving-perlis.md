# Plan: Lab_D1B_Settele.tex — Lab Slides for Settele (2022)

**Status:** COMPLETED  
**File to create:** `Slides/Lab_D1B_Settele.tex`  
**Session:** MN52233 · Day 1 · Session B (13:00–14:40, 100 min)

---

## Context

Session B is the hands-on complement to the D1A lecture on RCTs. Students have just learned the potential outcomes framework, randomization, and survey experiments conceptually. This lab anchors those ideas in a single published paper — Settele (2022), a clean survey experiment about gender wage gap beliefs and policy demand.

User specifications:
- STATA code: **full code blocks** on slides
- Scope: **ATE only** — randomization check + main OLS treatment effect
- Data: **pre-loaded on a shared drive** (students set working directory)

---

## Target Structure (~33 slides)

### Preamble (2 slides)
1. Title slide — `Lab_D1B_Settele.tex`, metadata matching D1A style
2. Session roadmap — three sections with time allocation

### Section 1: The Paper (7 slides + 1 transition)
3. Research question — do beliefs about the gender wage gap shape policy demand?
4. Motivation — the gender wage gap is contested; people hold very different beliefs about its size
5. Belief vs. reality — people systematically misestimate the gap; treatment provides accurate information
6. The key insight — if beliefs drive policy preferences, then exogenously shifting beliefs should shift policy support
7. Survey design overview — US online sample, ~1,500 respondents, MTurk-style recruitment
8. What Settele finds — treatment increases support for equal-pay policies (preview the punchline)
9. Where this fits — maps back to D1A: survey experiment, information treatment, ITT = ATE under full compliance
10. [Transition slide] Section 2

### Section 2: Research Design (8 slides + 1 transition)
11. Survey flow — three stages: (1) elicit prior beliefs, (2) randomize treatment/control, (3) measure policy outcomes
12. The information treatment — treatment group sees actual gender wage gap statistics; control sees unrelated filler
13. Outcome variables — policy support index: equal pay legislation, parental leave, pay transparency (3–5 items)
14. Identification assumption — random assignment ensures treatment ⊥ all pre-treatment characteristics
15. Potential outcomes formalized — Y_i(1) = policy support if treated; Y_i(0) = policy support if control; ATE = E[Y_i(1)−Y_i(0)]
16. Why this is not observational — contrast with just correlating beliefs with policy preferences (selection problem)
17. The estimator — simple difference-in-means / OLS with controls for precision
18. Threats to validity — demand effects, attrition, external validity (online sample); Settele's robustness checks
19. [Transition slide] Section 3

### Section 3: Hands-On Replication (13 slides)
20. Data overview — variables in the dataset: demographics, prior beliefs, treatment, post-beliefs, policy index
21. Step 0: Setup — `clear all`, `set more off`, `cd` to shared drive, `use settele2022.dta`
22. Step 1: Explore — `describe`, `tab treatment`, `sum` on key variables
23. Step 2: Visualise prior beliefs — histogram of respondents' belief about the gap; vertical line at truth
24. Step 3: Belief updating check — `ttest belief_post, by(treatment)` — does treatment shift beliefs?
25. Step 4: Randomization check (theory) — what to look for, why it matters
26. Step 5: Randomization check (code) — `ttest` or OLS of each baseline covariate on treatment; show balance table
27. Step 6: Main regression — OLS of policy support index on treatment dummy + controls; robust SEs
28. Step 7: Read the output — coefficient interpretation, magnitude (SD units or raw), significance
29. Step 8: Visualize the result — bar chart (treatment vs. control mean) using Okabe-Ito colors, `twoway bar`
30. Interpretation — connect back to potential outcomes: this coefficient is our ATE estimate
31. Discussion questions — 3 questions for group discussion (external validity, mechanism, policy implications)
32. Wrap-up — what we learned; preview D2A (RDD + DiD)

---

## STATA Code Conventions (per `stata-conventions.md`)

- `log using`, `set seed` where applicable
- All figures: `graphregion(color(white))`, Okabe-Ito hex colors
- Section dividers with `*--- Section N: ... ---*`
- No hardcoded absolute paths — students set `cd` themselves
- Results saved with `outreg2` or `esttab`

---

## Style Conventions (matching D1A)

- `\documentclass[aspectratio=169, 11pt]{beamer}`
- `\input{../Preambles/header.tex}`
- Date line: `MN52233 \quad Day 1 $\cdot$ Session B`
- All four box environments used: `keybox`, `examplebox`, `warningbox`, `intuitionbox`
- `\sectionslide{}{}` for section transitions
- No `\pause` or overlay commands
- `\source{}` for citations on figures
- STATA code rendered in `\texttt{}` or `verbatim` blocks

---

## Files to Create

| File | Action |
|------|--------|
| `Slides/Lab_D1B_Settele.tex` | Create from scratch |

No other files need modification (bibliography already has `Settele2022_gender`).

---

## Verification

Since no local LaTeX is available, verification = syntax check:
- All `\begin{frame}` balanced with `\end{frame}`
- All citations resolve to keys in `Bibliography_base.bib`
- All custom environments (`keybox`, etc.) match header.tex definitions
- No `\pause` commands
- STATA code blocks syntactically plausible
