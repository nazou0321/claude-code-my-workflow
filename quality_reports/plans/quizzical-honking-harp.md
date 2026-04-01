# Plan: D1A Lecture — Lab Experiments & RCTs
**Date:** 2026-04-01
**Status:** DRAFT
**Author:** Claude (plan mode)

---

## Context

Build the first lecture for MN52233: **D1A — Lab Experiments & Randomized Controlled Trials** (100 min, ~55 content slides + ~6 structural slides ≈ 61 total). This requires creating:
1. The shared Beamer theme (`Preambles/header.tex`) — used by all 6 sessions
2. The lecture itself (`Slides/Lecture_D1A_ExpRCT.tex`)
3. Bibliography entries for the 5 D1A readings + 3 replication papers

**Design parameters (from user):**
- Math: intuition-first, formulas as support (not the primary vehicle)
- Readings: motivating examples woven throughout, Settele briefly previewed at end
- Pace: ~55 content slides for 100 min (standard pace)
- Theme: dark navy + black, Okabe-Ito colorblind palette

---

## File 1: `Preambles/header.tex`

The shared preamble — all lecture `.tex` files will open with `\input{../Preambles/header.tex}`.

### Theme & Colors
- Base: Beamer `default` theme with fully custom colors
- Navy: `#1F3A5F` (headers, frame titles, rule lines)
- Accent: `#3A7EBF` (lighter navy for block backgrounds, secondary emphasis)
- Text: `#1A1A1A` (near-black body text)
- White: slide body background
- Okabe-Ito accent colors defined as named xcolor entries:
  - `\okabeblue` (#0072B2), `\okabeorange` (#E69F00), `\okabegreen` (#009E73)
  - `\okabesky` (#56B4E9), `\okabevermillion` (#D55E00), `\okabepink` (#CC79A7)
  - `\okabeyellow` (#F0E442)

### Layout
- Frame title: navy background, white bold text, rule at bottom
- Section slides: navy full background, white title (interstitial dividers)
- Footer: course code left · lecture title center · slide number right
- No navigation bars (clean for teaching)
- Fonts: default Beamer sans-serif (readable on projector)

### Custom Environments (defined in header.tex)
| Environment | Appearance | Use |
|-------------|------------|-----|
| `keybox` | Navy left border, light blue background | Key takeaways, definitions |
| `examplebox` | Orange left border, light orange background | Paper examples |
| `warningbox` | Vermillion left border, light red background | Common mistakes, caveats |
| `intuitionbox` | Green left border, light green background | Intuition statements |

### Packages loaded
`amsmath`, `amssymb`, `xcolor`, `graphicx`, `booktabs`, `tikz`, `natbib`, `hyperref`, `enumerate`, `ragged2e`

### Notation macros
- `\E{X}` → $\mathbb{E}[X]$
- `\Y{t}` → $Y(t)$ (potential outcome)
- `\ATE` → $\text{ATE}$
- `\ATT` → $\text{ATT}$
- `\indep` → $\perp\!\!\!\perp$ (independence)
- `\muted{text}` → gray text (for secondary items)

---

## File 2: `Bibliography_base.bib` — 8 entries to add

| Key | Reference |
|-----|-----------|
| `Banerjee2014_health` | Banerjee, Duflo & Hornbeck (2014), AER |
| `Bertrand2004_emily` | Bertrand & Mullainathan (2004), AER |
| `Jessoe2014_energy` | Jessoe & Rapson (2014), AER |
| `Settele2022_gender` | Settele (2022), AEJ:Policy |
| `Stantcheva2023_surveys` | Stantcheva (2023), Annual Review of Economics |
| `Braghieri2022_socialmedia` | Braghieri, Levy & Makarin (2022), AER |
| `Aghion2013_innovation` | Aghion, Van Reenen & Zingales (2013), AER |
| `AngristPischke2009` | Angrist & Pischke, *Mostly Harmless Econometrics* (2009) |

---

## File 3: `Slides/Lecture_D1A_ExpRCT.tex` — Lecture Structure

### Section 0: Opening (~3 structural slides)
1. **Title slide** — course, lecture title, date, institution
2. **Course roadmap** — 3 days, 6 sessions overview (mini table)
3. **Today's roadmap** — 6 sections outlined

### Section 1: Why Causal Inference? (~8 slides)
*Motivating question: "Does X cause Y, or do X and Y just move together?"*

4. The central question of program evaluation
5. A striking non-example: ice cream sales and drownings
6. A policy-relevant example: does education raise wages?
7. The Fundamental Problem of Causal Inference (Holland 1986) — we only see one world
8. Counterfactuals: what would have happened otherwise?
9. Selection bias — who self-selects into treatment?
   - `\examplebox`: Bertrand-Mullainathan setup: who applies to what jobs?
10. Why naive OLS comparisons mislead
11. **Section transition slide** (navy background): "The Solution: Run an Experiment"

### Section 2: Potential Outcomes Framework (~10 slides)
*Rubin Causal Model — the language of causal inference*

12. Two potential worlds for each unit: $Y_i(1)$ and $Y_i(0)$
13. The treatment indicator $D_i$; what we observe: $Y_i = D_i Y_i(1) + (1-D_i)Y_i(0)$
14. Individual treatment effect $\tau_i = Y_i(1) - Y_i(0)$ — never observed
15. Population quantities: ATE, ATT, ATC — what we usually want
    - `\intuitionbox`: ATT answers "did this policy work for people who got it?"
16. SUTVA — the hidden assumption
    - Part 1: No interference between units
    - Part 2: No multiple versions of treatment
17. SUTVA example: vaccine trials (spillovers via herd immunity)
18. Selection bias decomposition: $\E{Y|D=1} - \E{Y|D=0}$ = ATT + selection bias
19. **The key insight**: selection bias disappears under randomization
20. `\keybox`: Randomization makes $D \indep (Y(1), Y(0))$ → ATE identified
21. **Section transition slide**: "Types of Experiments"

### Section 3: Randomized Controlled Trials (~9 slides)
*Randomization as the gold standard*

22. What randomization does: treated and control groups are exchangeable
23. Balance: in expectation, all pre-treatment characteristics equal across groups
24. `\examplebox`: Bertrand & Mullainathan (2004) design
    - 5,000 resumes sent to real job ads in Chicago and Boston
    - Random assignment of "white-sounding" vs "Black-sounding" names
    - Same resume content → any callback difference = discrimination
25. Bertrand-Mullainathan: main finding (callback rates)
26. Why this is convincing: the randomization argument made explicit
27. `\examplebox`: Jessoe & Rapson (2014) — residential energy use
    - Random assignment of "Oracles" (real-time energy monitors)
    - Households with information save more energy
28. Jessoe-Rapson: what this tells us about information and behavior
29. Design choices that matter: unit of randomization, sample size, compliance
30. **Section transition slide**: "Beyond Standard RCTs"

### Section 4: Variations — Lab, Field, Survey Experiments (~10 slides)
*The experiment family tree*

31. Taxonomy overview: lab → field → survey (trade-off: control vs realism)
32. Lab experiments: high control, stylized setting
    - Subjects: often students; environment: researcher controls everything
    - Strength: isolate mechanism; Weakness: external validity
33. Field experiments: real world, real subjects
    - `\examplebox`: Banerjee, Duflo & Hornbeck (2014)
    - Bundled health insurance + microfinance in India
    - Key puzzle: low demand even with subsidies — no adverse selection if no demand
34. Field experiments: what makes them hard (contamination, attrition, scale)
35. Survey experiments: randomized information treatments in surveys
    - What makes it an *experiment*? The random variation in what respondents are shown
36. `\examplebox`: Stantcheva (2023) — how to design a survey experiment
    - Vignettes, information treatments, stated preference designs
    - Key principle: the survey itself is the randomization device
37. Survey experiment strengths: study beliefs, preferences, attitudes at scale
38. Survey experiment cautions: hypothetical bias, demand effects, inattention
39. `\examplebox`: Settele (2022) preview
    - Do beliefs about the gender wage gap affect policy demand?
    - Randomized information treatment about the true gap
    - *We'll replicate this in Session D1B*
40. `\keybox`: Choosing experiment type = trading off internal vs external validity

### Section 5: Complications (~9 slides)
*Real experiments don't always go as planned*

41. **Section transition slide**: "When Things Go Wrong"
42. Non-compliance: assigned ≠ treated
    - One-sided vs two-sided non-compliance
43. Intent-to-Treat (ITT): the conservative, always-identified estimate
44. LATE / TOT: the effect for compliers (those who comply because of the instrument)
    - `\intuitionbox`: LATE = ITT_Y / ITT_D — scale by compliance rate
45. Who are compliers? We can't identify them individually
46. Attrition: when subjects drop out
    - Random attrition: OK. Differential attrition: problem.
    - Bounding approach (Lee bounds)
47. Spillovers and SUTVA violations revisited
    - `\warningbox`: Household energy study — if neighbors talk, SUTVA fails
48. Randomization check (balance test): always report it; failure is a red flag
49. Hawthorne effects and demand effects: subjects change behavior when observed

### Section 6: Validity (~5 slides)
*What can we conclude from a well-run experiment?*

50. Internal validity: did we identify the causal effect *in this study*?
    - Threats: non-compliance, attrition, contamination
51. External validity: does it generalize?
    - To other populations? Other settings? Other time periods?
52. The LATE problem: we estimate effect for compliers, not for everyone
    - Sometimes LATE is exactly what we want (policy-relevant subgroup)
53. Aggregating evidence: meta-analysis, systematic reviews
54. `\keybox`: Experiments are the benchmark — but always ask "for whom?" and "where?"

### Section 7: Wrap-up (~4 slides)
55. Key concepts recap (one-slide bullet summary)
56. The causal inference toolkit: experiments are just one tool (preview of Days 2–3)
57. Session D1B preview: replicating Settele (2022) in STATA
    - Data structure, key variables, main regression
    - What to think about: how would you test the parallel-trends-equivalent here?
58. Thank you / Questions

---

## Verification Steps

1. Compile: `cd Slides && TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode Lecture_D1A_ExpRCT.tex` — must produce PDF without errors
2. BibTeX pass: `BIBINPUTS=..:$BIBINPUTS bibtex Lecture_D1A_ExpRCT` — all 8 citations resolve
3. Two more XeLaTeX passes — no undefined references
4. Visual check: open PDF, verify theme renders (navy headers, white body, custom boxes)
5. Slide count: confirm ~55–62 total slides
6. Quality score: `python scripts/quality_score.py` (target ≥ 80)

---

## Notes

- TikZ diagrams: at least one for Section 2 (potential outcomes illustration — two possible worlds for each unit). Simple diagram, no complex coordinates.
- The Settele (2022) preview in Section 4 is deliberately brief — it's the lab paper, so D1B covers it in depth.
- Stantcheva (2023) appears in Section 4 as methodological context for survey experiments, not as a standalone deep-dive.
- All paper results cited are at the level of "main finding" — no replication of specific tables.
