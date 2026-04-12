# CLAUDE.md — Academic Project Workflow Template

**Template:** Claude Code Academic Workflow
**Purpose:** General-purpose Claude Code setup — skills, rules, and hooks live here.
**Project-specific repos** have their own CLAUDE.md and `.claude/rules/`.

---

## Architecture

```
~/.claude/skills/     ← All shared skills (available in every project)
~/.claude/rules/      ← All general rules (active everywhere)

my-project/           ← This repo: template + reference copies
  .claude/skills/     ← Reference copies (for forking/sharing)
  .claude/rules/      ← Reference copies (general rules)
  .claude/agents/     ← Reference copies (generic agents)
  .claude/hooks/      ← Hooks (also copied to ~/.claude/hooks/ if needed)

[project-repo]/       ← e.g. MN52233, AMJ_RR, WagePanelty
  CLAUDE.md           ← Project-specific instructions
  .claude/rules/      ← Project-specific rules only
  .claude/agents/     ← Project-specific agents only
```

---

## Active Projects

| Repo | Path | Description |
|------|------|-------------|
| MN52233 | `~/Documents/GitHub/MN52233` | Causal Identification Strategies (PhD Year 1, Bath SoM) |

---

## Skills Quick Reference

Skills live in `~/.claude/skills/` and are available in all projects.

| Command | What It Does |
|---------|-------------|
| `/compile-latex [file]` | 3-pass XeLaTeX + bibtex |
| `/deploy [LectureN]` | Render Quarto + sync to docs/ |
| `/extract-tikz [LectureN]` | TikZ → PDF → SVG |
| `/proofread [file]` | Grammar/typo/overflow review |
| `/visual-audit [file]` | Slide layout audit |
| `/pedagogy-review [file]` | Narrative, notation, pacing review |
| `/review-r [file]` | R code quality review |
| `/qa-quarto [LectureN]` | Adversarial Quarto vs Beamer QA |
| `/slide-excellence [file]` | Combined multi-agent review |
| `/translate-to-quarto [file]` | Beamer → Quarto translation |
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

## Core Principles (apply to all projects)

- **Plan first** — enter plan mode before non-trivial tasks
- **Verify after** — compile/render and confirm output at the end of every task
- **Quality gates** — nothing ships below 80/100
- **Session logs** — create at `quality_reports/session_logs/YYYY-MM-DD_description.md`

---

## Adding a New Project

1. Create a new repo at `~/Documents/GitHub/[ProjectName]`
2. Copy relevant rules from `my-project/.claude/rules/` to `[ProjectName]/.claude/rules/`
3. Create `[ProjectName]/CLAUDE.md` with project-specific instructions
4. Add the project to the Active Projects table above
