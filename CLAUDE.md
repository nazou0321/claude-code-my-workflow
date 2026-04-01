# CLAUDE.MD -- Academic Project Development with Claude Code

**Project:** MN52233 — Causal Identification Strategies (PhD Year 1)
**Institution:** University of Bath, School of Management
**Branch:** main

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- compile/render and confirm output at the end of every task
- **Single source of truth** -- Beamer `.tex` is authoritative; Quarto `.qmd` derives from it (Quarto currently deferred)
- **Quality gates** -- nothing ships below 80/100
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong → right` to MEMORY.md

---

## Folder Structure

```
MN52233/
├── CLAUDE.MD                    # This file
├── .claude/                     # Rules, skills, agents, hooks
├── Bibliography_base.bib        # Centralized bibliography
├── Figures/                     # Figures and images
├── Labs/                        # STATA do-files (one per lab session)
├── Preambles/header.tex         # LaTeX headers
├── Slides/                      # Beamer .tex files
├── Quarto/                      # RevealJS .qmd files + theme (dormant)
├── docs/                        # GitHub Pages (auto-generated, dormant)
├── scripts/                     # Utility scripts
├── quality_reports/             # Plans, session logs, merge reports
├── explorations/                # Research sandbox (see rules)
├── templates/                   # Session log, quality report templates
└── master_supporting_docs/      # Papers and existing slides
```

---

## Commands

```bash
# LaTeX (3-pass, XeLaTeX only)
cd Slides && TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex
BIBINPUTS=..:$BIBINPUTS bibtex file
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex

# Run a STATA do-file (batch mode)
cd Labs && stata -b do Lab_D1B_Settele2022.do

# Deploy Quarto to GitHub Pages (dormant — activate when needed)
# ./scripts/sync_to_docs.sh LectureN

# Quality score
python scripts/quality_score.py Quarto/file.qmd
```

---

## Visual Standards

- **Theme:** Dark navy headers (`#003B6F` range) + black body text; colorblind-safe throughout
- **Figures (Okabe-Ito palette — mandatory for all plots and diagrams):**
  - Blue `#0072B2` · Orange `#E69F00` · Green `#009E73` · Sky `#56B4E9`
  - Vermillion `#D55E00` · Pink `#CC79A7` · Yellow `#F0E442`
- **No red/green combinations**
- Applied to: Beamer theme, all STATA `graph export`, any TikZ diagrams

---

## Quality Thresholds

| Score | Gate | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for deployment |
| 95 | Excellence | Aspirational |

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/compile-latex [file]` | 3-pass XeLaTeX + bibtex |
| `/deploy [LectureN]` | Render Quarto + sync to docs/ (dormant) |
| `/extract-tikz [LectureN]` | TikZ → PDF → SVG |
| `/proofread [file]` | Grammar/typo/overflow review |
| `/visual-audit [file]` | Slide layout audit |
| `/pedagogy-review [file]` | Narrative, notation, pacing review |
| `/review-r [file]` | R code quality review |
| `/qa-quarto [LectureN]` | Adversarial Quarto vs Beamer QA (dormant) |
| `/slide-excellence [file]` | Combined multi-agent review |
| `/translate-to-quarto [file]` | Beamer → Quarto translation (dormant) |
| `/validate-bib` | Cross-reference citations |
| `/devils-advocate` | Challenge slide design |
| `/create-lecture` | Full lecture creation |
| `/commit [msg]` | Stage, commit, PR, merge |
| `/lit-review [topic]` | Literature search + synthesis |
| `/review-paper [file]` | Manuscript review |
| `/learn [skill-name]` | Extract discovery into persistent skill |
| `/context-status` | Show session health + context usage |
| `/deep-audit` | Repository-wide consistency audit |

---

## Beamer Custom Environments

| Environment          | Appearance                                  | Use Case                          |
|----------------------|---------------------------------------------|-----------------------------------|
| `keybox[Title]`      | Navy title bar (white text), light blue body | Key definitions, core results     |
| `examplebox[Title]`  | Dark orange title bar (white text), light orange body | Paper examples, empirical cases |
| `warningbox[Title]`  | Vermillion title bar (white text), light red body | Caveats, assumption violations   |
| `intuitionbox[Title]`| Green title bar (white text), light green body | Intuition statements             |

## Quarto CSS Classes

<!-- Dormant — populate when Quarto is activated -->

| Class              | Effect        | Use Case       |
|--------------------|---------------|----------------|
| `[.your-class]`    | [Description] | [When to use]  |

---

## Current Project State

| Lecture | Beamer | Quarto | STATA Lab | Key Content |
|---------|--------|--------|-----------|-------------|
| D1A: Lab Exp + RCT | `Lecture_D1A_ExpRCT.tex` | -- | -- | Potential outcomes, SUTVA, randomization |
| D1B: Lab (Settele 2022) | `Lab_D1B_Settele.tex` | -- | `Lab_D1B_Settele2022.do` | Survey experiment replication |
| D2A: RDD + DiD | `Lecture_D2A_RDD_DiD.tex` | -- | -- | Parallel trends, continuity, PT tests |
| D2B: Lab (Braghieri 2022) | `Lab_D2B_Braghieri.tex` | -- | `Lab_D2B_Braghieri2022.do` | DiD replication, staggered rollout |
| D3A: IV + PSM | `Lecture_D3A_IV_PSM.tex` | -- | -- | Exclusion restriction, overlap, IPW |
| D3B: Lab (Aghion 2013) | `Lab_D3B_Aghion.tex` | -- | `Lab_D3B_Aghion2013.do` | IV replication, instrument validity |

### Replication Papers
- **Day 1:** Settele, S. (2022). How do beliefs about the gender wage gap affect the demand for public policy? *AEJ: Economic Policy*, 14(2), 475–508.
- **Day 2:** Braghieri, L., Levy, R. E., & Makarin, A. (2022). Social media and mental health. *American Economic Review*, 112(11), 3660–3693.
- **Day 3:** Aghion, P., Van Reenen, J., & Zingales, L. (2013). Innovation and institutional ownership. *American Economic Review*, 103(1), 277–304.
