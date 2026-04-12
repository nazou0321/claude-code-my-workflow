# Plan: SMJ_RR1 — Empirical Responses (All Concerns)

**Status:** DRAFT
**Date:** 2026-04-12
**Output directory:** `/Users/nazou/Dropbox/SMJ_RR1_dup/response/`

---

## Context

The paper has completed all major new empirical analyses. The Mar22 Word file has partial responses — some concerns well-addressed, others have placeholders or are missing entirely. The April 9 empirics file contains the latest results, including two corrections that haven't been applied to the draft yet:
1. Knowledge structure measures (decomposability, coupling intensity) are **significant** in Table 8 — the March draft incorrectly calls them "insignificant"
2. High-tech subsample (Table 7) shows stronger BUS effects and weak STEM signals on novel/breakthrough patents

Goal: produce a complete, polished, publication-ready set of empirical responses that can be pasted into the Word response letter.

---

## Concern Inventory

### AE Letter (III: Methods)

| ID | Concern | Current status | Action |
|----|---------|---------------|--------|
| AE.IIIa | Mixes discovery analysis with causal inference statements | Not drafted | Write from scratch |
| AE.IIIb | IV (HSR exclusion restriction) + DID (political access) | IV drafted ✓; DID partial | Complete DID; cross-ref with R1.Q12/Q13 |
| AE.IIIc | Linking board → intermediate steps → patents | Not drafted | Write from scratch (use MDA + inventor data) |
| AE.IIId | Measurement: descriptive stats, patent jurisdiction, family size, controls, matching | Partially addressed across R1/R2 | Write unified AE response cross-referencing sub-responses |
| AE.IIIe | Mechanism evidence insufficient (interview limitation) | Not drafted | Write (acknowledge + corroboration with quantitative evidence) |

### Reviewer 1

| ID | Concern | Current status | Action |
|----|---------|---------------|--------|
| R1.Q8 | STEM null due to lack of variation | Drafted ✓ | Verify numbers match April 9 |
| R1.Q9a | Board size descriptive stat (0.37) | Drafted ✓ | Keep |
| R1.Q9b | Tenure typo (0.15 months) | Drafted ✓ | Keep |
| R1.Q9c | Pre-sample mean transformation | Drafted ✓ | Keep |
| R1.Q10 | Multiple patent offices → CNIPA | Drafted ✓ | Verify numbers |
| R1.Q11 | How identified "strategy" publications via OpenAlex | Incomplete: "More detailed to be added" | Complete the description |
| R1.Q12 | HSR instrument → new term-limit IV | Drafted ✓, good numbers | Verify vs April 9; note only patent apps significant under IV |
| R1.Q13 | DID: drop may reflect political access loss, not knowledge | **Not drafted at all** | Write from scratch — most dangerous concern |

### Reviewer 2

| ID | Concern | Current status | Action |
|----|---------|---------------|--------|
| R2.Maj2a | Forward citations + breakthrough patents as new DVs | Drafted ✓ | Keep |
| R2.Maj2b | Patent entry into new tech sectors | Done in empirics, not in response | Write response |
| R2.Maj2c | Knowledge structure (Yayavaram) | **Draft says "insignificant" but April 9 Table 8 shows significant** | Correct and rewrite |
| R2.Maj2d | Sales/profit outcomes | Drafted with NZ note "(not sure whether we should include)" | Resolve and write clean response |
| R2.Min1 | Matching procedure appendix | Placeholder "Appendix XXX" | Write proper pointer (confirm appendix title) |
| R2.Min2 | Family size correlation (r=0.96) | Drafted but placeholder "(ADD EXPLANATIONS WHY THIS MAY BE THE CASE)" | Complete explanation |
| R2.Min3 | Board controls (human capital, social capital, diversity) | Drafted ✓ | Keep |
| R2.Min4 | Balanced STEM analysis (robustness checks for STEM null) | Partial (dummy measures); high-tech subsample results not yet referenced | Write complete response including high-tech finding |
| R2.Min5 | HSR instrument (suggest using universities not cities) | Drafted: abandoned HSR entirely, new IV | Keep / reference R1.Q12 |
| R2.Min6 | DID less defensible (only affects admin scholars with political capital) | Partial analysis done; response not written | Write response (coordinate with R1.Q13) |
| R2.Min7 | Qualitative: only interviewed BUS scholars, not firm executives | Not drafted | Write response (acknowledge + corroboration strategy) |
| R2.Min8 | Government access as alternative explanation | Partial | Write clean acknowledgment + limitation |

---

## Output Structure

Two files:

### File 1: `response/review_tracker.md`
Master tracker — all concerns (including theory), status, priority, and cross-references.

### File 2: `response/empirical_responses_draft.md`
All empirical responses in order matching the Word file structure. Organized:
1. Responses to AE (III.a–e)
2. Responses to Reviewer 1 (Q8–Q13)
3. Responses to Reviewer 2 (Major 2a–d; Minor 1–8)

Format per response:
```
## [ID]: [Short title]

**Addressing:** [reviewer + exact concern]

[Full polished prose response — ready to paste into Word]

**Manuscript changes:**
- [p. X, Section Y: description of change]
```

---

## Sequencing (within the writing session)

Write in this order — most dangerous first, then complete left to right:

1. **R1.Q13 + R2.Min6** — DID / political access (write together since overlapping)
2. **AE.IIIa** — Type of inference (sets tone for how we frame all causal claims)
3. **AE.IIIc** — Linking board → patents (mechanism chain; draws on MDA + inventor data)
4. **AE.IIIe** — Mechanism evidence + interview limitation
5. **R2.Maj2c** — Knowledge structure correction (significant, not insignificant)
6. **R2.Min4** — Balanced STEM analysis incl. high-tech subsample
7. **R2.Maj2b** + **R2.Maj2d** — Remaining DV responses
8. **R1.Q11** — OpenAlex classification completion
9. **R2.Min2** — Family size explanation
10. **R2.Min7** + **R2.Min8** — Qualitative limitation + government access
11. **AE.IIId** — Unified AE measurement response
12. **AE.IIIb** — AE methods summary (cross-references R1.Q12, R1.Q13)
13. **Review/verify** — R1.Q8, Q9a-c, Q10, Q12; R2.Min1, Min3, Min5 — check numbers against April 9

---

## Key Analytical Decisions (built into the responses)

**On the DID (R1.Q13 / R2.Min6):**
- Acknowledge political access is a legitimate alternative channel that we cannot fully rule out
- Present the BUS-all vs BUS-Admin resignation comparison as evidence the effect is not driven by the admin/political subgroup
- Reframe DID as *corroborating* rather than *identifying* evidence — the IV is the main causal identification
- Acknowledge government access as a limitation (R2 already suggested this)

**On inference type (AE.IIIa):**
- Clearly separate: IV analysis = causal claim; all other analyses (MDA, inventor structure, knowledge structure, contingency analyses) = exploratory/descriptive, consistent with the theory
- Commit to reformulating language in revision to reflect this

**On knowledge structure (R2.Maj2c):**
- Update: Table 8 (April 9) shows significant effects of BUS scholars on solo inventor share (β=-0.005, p=0.006), knowledge base decomposability (β=0.002, p=0.007), and coupling intensity (β=-0.002, p=0.004) — all in the predicted direction
- This is a stronger result than the March draft acknowledged

**On IV under CNIPA (R1.Q12 note):**
- Acknowledge that under the new IV, only patent applications are significant (not forward citations/breakthrough patents) — be transparent about this
- Frame: the IV provides causal identification for the quantity effect; other quality measures use Poisson FE with pre-sample controls (standard in this literature)

**On STEM in high-tech (R2.Min4):**
- High-tech subsample shows marginal STEM effects on novel patents (β=0.287, p=0.098) and breakthrough patents (β=0.312, p=0.054) in baseline — this is interesting but loses significance with controls
- Report honestly: STEM effects are domain-specific and fragile; consistent with the board/project distinction (R1.Q1)

---

## Verification

Before saving responses:
- [ ] All coefficient values match either the March or April 9 empirics file (no fabricated numbers)
- [ ] All table references use actual table numbers from the empirics file
- [ ] No responses promise manuscript changes that conflict with the agreed framing
- [ ] DID response is consistent with R2.Min8 (government access as limitation)
- [ ] Inference type framing (AE.IIIa) is consistent across all responses that make causal claims
- [ ] Score >= 90/100 on quality-gates rubric before saving

---

## What This Plan Does NOT Cover

- AE.I (framing/motivation) → theory round
- AE.II (strategic knowledge construct) → theory round
- R2.Major.1 (structural mismatch) → theory round
- R2.Major.3/4 (post-hoc theory, discussion restructure) → theory round
- R1 theory concerns Q1–Q7 → theory round
