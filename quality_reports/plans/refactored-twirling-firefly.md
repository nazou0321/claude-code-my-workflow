---
status: COMPLETED
title: WagePanelty_NGOs — Workflow Initialization
created: 2026-04-05
project: WagePanelty_NGOs
---

# Context

The user is launching a new research paper project called **WagePanelty_NGOs** — a causal identification study asking whether early NGO employment causes a long-term wage penalty. A 1-pager has already been submitted to the Babson conference; the immediate deliverable is a **6-pager abridged paper**.

The project folder already exists on OneDrive (`/Users/nazou/Library/CloudStorage/OneDrive-Personal/Wage Panelty in NGOs/`) and contains only Word documents (drafts, Babson submissions, idea sketches). No `.claude/` config, no code, no bibliography file yet.

The stack is **Stata + Word/Quarto** (same pattern as AMJ_RR, not the LaTeX/Beamer pattern of MN52233). The coauthor collaborates via OneDrive.

This plan initializes the Claude Code workflow for the project by:
1. Setting up `.claude/` configuration adapted from `my-project`
2. Creating a project-specific `CLAUDE.md`
3. Connecting Zotero as the bibliography source
4. Creating the quality_reports/ directory structure
5. Saving project memory and an initial session log

---

# Scope

**Project folder:** `/Users/nazou/Library/CloudStorage/OneDrive-Personal/Wage Panelty in NGOs/`
(referred to as `$PROJECT` below)

**Source template:** `/Users/nazou/my-project/` (the MN52233 repo)

---

# Phase 1 — Read Existing Drafts

Before configuring anything, read the key Word docs to extract:
- Research question, hypothesis, data, identification strategy
- Babson conference format requirements (from the example abridged paper)
- Current state of the argument

Files to read:
- `$PROJECT/Babson/Abstract Babson2025_final.docx` — submitted abstract
- `$PROJECT/Babson/Summary Babson2026.docx` — 1-pager submitted
- `$PROJECT/Babson/Previous example Abridged paper Babson24.docx` — format reference
- `$PROJECT/The hidden costs of being altruistic.docx` — paper draft
- `$PROJECT/Idea schetch Wage Panelty in NGOs_MG.docx` — idea sketch
- `$PROJECT/My claude prompts for WagePanelty_NGOs.docx` — any prior Claude instructions

---

# Phase 2 — Zotero Bibliography Integration

**Answer to user's Zotero question:**

The simplest and most reliable approach is a **BibTeX export from Zotero**:

### Option A — Manual export (simplest)
1. In Zotero: File → Export Library → Format: BibTeX → Save as `References.bib` in the project folder
2. Re-export whenever new references are added
3. Claude can read and search the .bib file directly

### Option B — Better BibTeX auto-export (recommended for active projects)
1. Install the Better BibTeX (BBT) plugin for Zotero (free, zotero.org/support/plugins)
2. In Zotero: Edit → Preferences → Better BibTeX → set citation key format
3. Right-click your WagePanelty_NGOs collection → Export Collection → Better BibTeX → tick "Keep updated"
4. Save to `$PROJECT/References.bib`
5. BBT auto-updates the file whenever you add/edit references in Zotero

**Recommendation:** Option B, because the project is active and references will grow. Once set up, I can always read the latest `References.bib` without you doing anything.

**Action required from user:** Export or auto-export the Zotero collection to `$PROJECT/References.bib` before the lit-review and writing phases begin.

---

# Phase 3 — Create Project Infrastructure

## 3a. Directory structure to create

```
Wage Panelty in NGOs/
├── CLAUDE.md                        # Project config (to create)
├── References.bib                   # Zotero export (user action)
├── Babson/                          # Existing — conference submissions
├── Data/                            # Stata datasets (.dta, .csv)
├── Analysis/                        # Stata do-files
├── Output/                          # Tables, figures exported from Stata
├── Writing/                         # Main manuscript drafts
├── quality_reports/
│   ├── plans/
│   ├── session_logs/
│   ├── specs/
│   └── merges/
└── .claude/
    ├── settings.json
    ├── rules/
    ├── skills/
    └── agents/
```

## 3b. CLAUDE.md

Create a project-specific `CLAUDE.md` covering:
- Project: WagePanelty_NGOs — Long-term wage penalty of early NGO employment
- Institution: University of Bath, School of Management
- Coauthor collaboration via OneDrive
- Folder structure (as above)
- Commands: Stata batch mode, pandoc for docx→md conversion, python3 for quality scoring
- Visual standards: Okabe-Ito palette (mandatory), colorblind-safe, publication-ready
- Quality thresholds: 80/90/95
- Project state table: current deliverable = 6-pager Babson abridged paper
- Beamer custom environments: N/A (Word-based writing)
- Bibliography: References.bib (Zotero export)

## 3c. .claude/settings.json

Allow:
```json
{
  "permissions": {
    "allow": [
      "Bash(stata*)",
      "Bash(python3*)",
      "Bash(pandoc*)",
      "Bash(git*)",
      "Bash(ls*)",
      "Bash(mkdir*)",
      "Bash(cp*)",
      "Bash(mv*)"
    ]
  }
}
```

## 3d. Rules to copy/adapt from my-project

Copy verbatim (universal):
- `plan-first-workflow.md`
- `orchestrator-protocol.md`
- `session-logging.md`
- `verification-protocol.md`
- `meta-governance.md`
- `exploration-fast-track.md`

Create new:
- `word-handling.md` — pandoc-based docx↔md conversion, track-changes protocol, coauthor sync via OneDrive
- `stata-conventions.md` — do-file structure, seed before simulations, graph export standards (Okabe-Ito in Stata), log file management

Remove (Beamer/LaTeX-specific):
- `beamer-quarto-sync.md`
- `tikz-visual-quality.md`
- `replication-protocol.md` (MN52233-specific)
- `stata-replication.md` (MN52233-specific, if present)

## 3e. Skills to copy from my-project

Copy (universal, keep as-is):
- `review-paper.md`
- `lit-review.md`
- `proofread.md`
- `commit.md`
- `learn.md`
- `context-status.md`
- `deep-audit.md`
- `interview-me.md`
- `research-ideation.md`

Remove (Beamer/LaTeX-specific):
- `compile-latex.md`
- `deploy.md`
- `extract-tikz.md`
- `translate-to-quarto.md`
- `qa-quarto.md`
- `create-lecture.md`

Create new:
- `write-section.md` — guided section-by-section drafting for the 6-pager (outline → draft → review loop)
- `validate-refs.md` — cross-check in-text citations against References.bib (like validate-bib but for Word/Quarto)

## 3f. Agents to copy/adapt

Copy and adapt:
- `proofreader.md` — keep (universal)
- `domain-reviewer.md` — **adapt** the 5 review lenses for labor economics / NGO sector research:
  1. Causal identification validity (instrument validity, parallel trends, selection bias)
  2. Wage penalty measurement (decomposition methods, selection into NGO sector)
  3. External validity (generalizability of early career effects)
  4. Citation fidelity (do claims match cited sources)
  5. Policy relevance (are implications for NGO sector clearly drawn)

Remove (Beamer-specific):
- `slide-auditor.md`
- `pedagogy-reviewer.md`
- `tikz-reviewer.md`
- `beamer-translator.md`
- `quarto-critic.md`
- `quarto-fixer.md`

Keep (useful for paper):
- `r-reviewer.md` → repurpose as `stata-reviewer.md` for do-file quality

---

# Phase 4 — Memory and Session Log

## Memory entry for this project

Create `/Users/nazou/.claude/projects/-Users-nazou-my-project/memory/project_wagepanelty_ngos.md`:
- Project name, RQ, identification strategy, data source
- Coauthor name (to be filled once known)
- Babson conference deadline and 6-pager requirements
- OneDrive path
- Zotero setup status

Update `MEMORY.md` index with pointer to new file.

## Initial session log

Create `$PROJECT/quality_reports/session_logs/2026-04-05_project-initialization.md` using the session-log template. Document:
- Goal: set up workflow for WagePanelty_NGOs
- Files created
- Zotero action required
- Open questions (data source, identification strategy details, coauthor name)

---

# Phase 5 — Read Existing Drafts for 6-Pager Planning

After setup, read the existing Word docs (via pandoc conversion to text) and:
- Extract the current argument structure
- Identify the identification strategy (DiD? IV? Panel FE?)
- Map the Babson 6-pager format from the example
- Present a structured outline for the 6-pager for user approval

This sets up the *next* plan (6-pager drafting), which will be a separate planning session.

---

# Verification

After implementation:
1. Confirm all directories exist under `$PROJECT`
2. Confirm `.claude/settings.json` is valid JSON
3. Confirm `CLAUDE.md` has no unfilled placeholders
4. Confirm session log is saved
5. Confirm memory index is updated
6. Read back key files to user for approval

---

# Open Questions (to confirm before or during implementation)

1. **Coauthor name** — who is the coauthor? (For memory and collaboration config)
2. **Data source** — what dataset are you using? (Panel survey data? Admin data?)
3. **Identification strategy** — what's the causal design? (DiD? IV? Panel FE with matching?)
4. **Babson 6-pager deadline** — when is the submission due?
5. **Zotero collection name** — what's the Zotero collection or library for this project?
6. **Writing format preference** — will the 6-pager be in Word (for coauthor) or Quarto (for polished PDF)?

These can be answered now or filled in during the session log step.

---

# Execution Order

1. Read existing Word docs (Phase 1)
2. Create directory structure (Phase 3a)
3. Create CLAUDE.md (Phase 3b)
4. Create .claude/settings.json (Phase 3c)
5. Copy/adapt rules (Phase 3d)
6. Copy/adapt skills (Phase 3e)
7. Copy/adapt agents (Phase 3f)
8. Create memory entry + update index (Phase 4)
9. Create initial session log (Phase 4)
10. Present Zotero instructions to user (Phase 2)
11. Extract argument from drafts + propose 6-pager outline (Phase 5) — *after user reviews setup*
