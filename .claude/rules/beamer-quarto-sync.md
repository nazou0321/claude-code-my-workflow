---
paths:
  - "Slides/**/*.tex"
  - "Quarto/**/*.qmd"
---

# Beamer → Quarto Auto-Sync Rule (MANDATORY)

**Every edit to a Beamer `.tex` file MUST be immediately synced to the corresponding Quarto `.qmd` file — automatically, without the user asking.** This is non-negotiable.

## The Rule

When you modify a Beamer `.tex` file, you MUST also apply the equivalent change to the Quarto `.qmd` (if it exists) **in the same task**, before reporting completion. Do NOT wait to be asked. Do NOT just "flag the drift." Just do it.

## Lecture Mapping

<!-- Quarto deferred: all Quarto entries stay "--" until web publishing is activated -->
| Lecture | Beamer | Quarto |
|---------|--------|--------|
| D1A: Lab Exp + RCT | `Slides/Lecture_D1A_ExpRCT.tex` | -- |
| D1B: Lab (Settele 2022) | `Slides/Lab_D1B_Settele.tex` | -- |
| D2A: RDD + DiD | `Slides/Lecture_D2A_RDD_DiD.tex` | -- |
| D2B: Lab (Braghieri 2022) | `Slides/Lab_D2B_Braghieri.tex` | -- |
| D3A: IV + PSM | `Slides/Lecture_D3A_IV_PSM.tex` | -- |
| D3B: Lab (Aghion 2013) | `Slides/Lab_D3B_Aghion.tex` | -- |
<!-- When activating Quarto: add .qmd path and set sync rule to fire -->

## Workflow (Every Time)

1. Apply fix to Beamer `.tex`
2. **Immediately** apply equivalent fix to Quarto `.qmd`
3. Compile Beamer (3-pass xelatex)
4. Render Quarto (`./scripts/sync_to_docs.sh LectureN`)
5. Only then report task complete

## LaTeX → Quarto Translation Reference

| Beamer | Quarto Equivalent |
| ------ | ----------------- |
| `\muted{text}` | `[text]{style="color: #525252;"}` |
| `\key{text}` | `[**text**]{.emorygold}` |
| `\textcolor{positive}{text}` | `[text]{.positive}` |
| `\textcolor{negative}{text}` | `[text]{.negative}` |
| `\item text` | `- text` |
| `\begin{highlightbox}` | `::: {.highlightbox}` |
| `\begin{methodbox}` | `::: {.methodbox}` |
| `$formula$` | `$formula$` (same) |

## When NOT to Sync

- Quarto file doesn't exist yet
- Change is LaTeX-only infrastructure (preamble, theme files)
- Explicitly told to skip Quarto sync

## Enforcement

Before marking any Beamer editing task as complete, check:
> "Did I also update the Quarto file?"

If the answer is no and a Quarto file exists, **you are NOT done.**

## When to Update This Table

After creating a new Quarto translation, add it to the mapping table above.
