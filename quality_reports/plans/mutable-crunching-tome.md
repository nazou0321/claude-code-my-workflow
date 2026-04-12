# Plan: Adapt Claude Code Workflow for ENT Co-optation AMJ_RR

**Status:** COMPLETED  
**Created:** 2026-04-02  
**Author:** Claude Code  

---

## Context

The user has an AMJ revision (ENT Co-optation paper) located at:
`/Users/nazou/Library/CloudStorage/OneDrive-Personal/ERD mobility/2026_AMJ Submission/RR1`

The existing Claude Code workflow in this repo was built for lecture slides (MN52233). It needs to be adapted for a Word-based paper revision project with a completely different stack and workflow:

- **No LaTeX, no Stata, no R** — everything in Word .docx
- **Primary tasks:** Analyze reviewer comments, draft response letter, literature synthesis
- **Domain:** Entrepreneurship / institutional theory (co-optation)
- **Setup goal:** Work directly in the OneDrive folder; this repo provides the template/source

The RR1 folder currently contains:
- `ENT Co-optation 20260126_blind.docx` — manuscript (~4.5 MB)
- `Attached file- Decision-Letter-AMJ-2026-0114-For-authors.docx` — decision + reviewer comments
- `AMJ Comments and responses.docx` — draft response tracker
- `My claude prompts.docx` — user's previous Claude prompts (reference)
- `Ricks reflectin.docx` / `Ricks reflection.docx` — co-author notes
- `Chen Guoheng.docx` — likely a reference/person note
- `Papers suggested by reviewers/` — 7 PDFs (Bradley & Klein 2016, deJordy 2020, Minniti 2008, Peng 2001, Puffer & McCarthy 2001, Von Briel 2025, EBSCO fulltext)

---

## Approach

### Phase 1: Initialize project structure in RR1 (5 files)

Create the minimal project scaffold directly in the OneDrive folder:
- `CLAUDE.md` — paper-specific config (fills all MN52233 placeholders with AMJ_RR context)
- `.gitignore` — exclude OneDrive temp files, .DS_Store; track .docx or not (TBD)
- `quality_reports/plans/.gitkeep`
- `quality_reports/session_logs/.gitkeep`
- `quality_reports/specs/.gitkeep`
- `quality_reports/merges/.gitkeep`
- `response/` — folder for Claude's markdown draft outputs

**Decision: No git init.** OneDrive provides sync/versioning; git on OneDrive causes conflicts. Claude will produce markdown drafts in `response/` folder (Word-readable via pandoc conversion).

### Phase 2: Create .claude/ config in RR1 (6 files)

A lean `.claude/` tailored for paper revision — only what's needed, no lecture-slide infrastructure:

**settings.json** — Permissions:
- `pandoc` (read/convert .docx → text)
- `python3` (python-docx for extraction)
- `textutil` (macOS built-in .docx → text)
- Standard file ops (ls, wc, mkdir, open)
- No xelatex, no bibtex, no quarto

**rules/** (4 rules, not 21):

1. `word-handling.md` — NEVER directly edit .docx files. Read via `pandoc -t markdown file.docx`. All Claude outputs go to `response/YYYY-MM-DD_*.md` files. User copies/pastes into Word manually.
2. `review-response-protocol.md` — Standard structure for point-by-point responses: quote reviewer verbatim → classify concern (major/minor/clarification) → draft response → flag manuscript location of change. Track all comments in a master tracker.
3. `plan-first-workflow.md` — Adapted version: same spec-then-plan protocol but without LaTeX verification steps.
4. `session-logging.md` — Identical to this repo's version (already generic).

**No orchestrator-protocol.md needed** — paper revision tasks are sequential and user-driven, not parallel compilation pipelines.

### Phase 3: Create paper-specific CLAUDE.md

Key sections to fill:

```
Project: ENT Co-optation — AMJ Revision Round 1
Journal: Academy of Management Journal
Domain: Entrepreneurship / Institutional Theory
Stack: Word documents (no code)
Primary tasks: Review analysis, response drafting, literature synthesis

Key files:
  Manuscript: ENT Co-optation 20260126_blind.docx
  Decision letter: Attached file- Decision-Letter-AMJ-2026-0114-For-authors.docx
  Response tracker: AMJ Comments and responses.docx
  Co-author notes: Ricks reflection.docx
  Reviewer papers: Papers suggested by reviewers/

Commands:
  Read a Word file: pandoc -t markdown "file.docx" | head -200
  Read reviewer PDFs: python scripts/extract_pdf.py "filename.pdf"
```

Quality thresholds:
- Response drafts: 85+ before sharing with co-authors
- Final response letter: 90+ before submission

### Phase 4: Copy minimal skills from this repo

Copy 4 skills from `/Users/nazou/my-project/.claude/skills/` into `RR1/.claude/skills/`:
- `lit-review/` — already generic, use as-is
- `review-paper/` — adapt description for AMJ revision context
- `context-status/` — keep as-is
- `learn/` — keep as-is

Create 1 new skill:
- `analyze-reviews/` — Read decision letter, extract all reviewer comments, classify by type (major theory, major empirics, major positioning, minor), create structured tracker markdown

### Phase 5: Update memory in this repo

Add to `/Users/nazou/.claude/projects/-Users-nazou-my-project/memory/`:
- `project_amj_rr.md` — Paper context, key files, domain, co-authors
- Update `MEMORY.md` index pointer

---

## Critical Files to Create

| File | Location | Purpose |
|------|----------|---------|
| `CLAUDE.md` | RR1/ | Master config for paper project |
| `.claude/settings.json` | RR1/.claude/ | Permissions (pandoc, textutil, python3) |
| `.claude/rules/word-handling.md` | RR1/.claude/rules/ | Never edit .docx; read via pandoc |
| `.claude/rules/review-response-protocol.md` | RR1/.claude/rules/ | Point-by-point response structure |
| `.claude/rules/plan-first-workflow.md` | RR1/.claude/rules/ | Adapted (no LaTeX verify step) |
| `.claude/rules/session-logging.md` | RR1/.claude/rules/ | Session logs in quality_reports/ |
| `.gitignore` | RR1/ | .DS_Store, OneDrive temps, __pycache__ |
| `response/.gitkeep` | RR1/response/ | Folder for Claude's markdown output |
| `quality_reports/plans/.gitkeep` | RR1/quality_reports/ | Plans |
| `quality_reports/session_logs/.gitkeep` | RR1/quality_reports/ | Session logs |
| `quality_reports/specs/.gitkeep` | RR1/quality_reports/ | Specs |
| `.claude/skills/lit-review/SKILL.md` | RR1/.claude/skills/ | Copy from this repo |
| `.claude/skills/review-paper/SKILL.md` | RR1/.claude/skills/ | Copy + adapt from this repo |
| `.claude/skills/analyze-reviews/SKILL.md` | RR1/.claude/skills/ | New: parse + classify reviewer comments |
| `.claude/skills/context-status/SKILL.md` | RR1/.claude/skills/ | Copy from this repo |
| `.claude/skills/learn/SKILL.md` | RR1/.claude/skills/ | Copy from this repo |
| memory/project_amj_rr.md | ~/.claude/projects/.../memory/ | Paper project memory |

---

## Verification

After implementation, verify by opening a new Claude Code session in the RR1 folder:
1. Check CLAUDE.md loads correctly (project name, file list visible)
2. Run `pandoc -t markdown "Attached file- Decision-Letter-AMJ-2026-0114-For-authors.docx" | head -50` — should render text
3. Confirm `response/` folder exists
4. Confirm `quality_reports/` structure exists
5. Test `/analyze-reviews` skill trigger is recognized

---

## What This Does NOT Do

- Does NOT git-init the OneDrive folder (OneDrive = version control)
- Does NOT copy lecture-slide rules (no Beamer, TikZ, STATA rules)
- Does NOT install python-docx (uses `pandoc` + `textutil` instead — already on macOS)
- Does NOT modify the MN52233 CLAUDE.md in this repo (left intact for course work)
