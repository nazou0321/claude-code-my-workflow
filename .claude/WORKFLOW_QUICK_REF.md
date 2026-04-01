# Workflow Quick Reference

**Model:** Contractor (you direct, Claude orchestrates)

---

## The Loop

```
Your instruction
    ↓
[PLAN] (if multi-file or unclear) → Show plan → Your approval
    ↓
[EXECUTE] Implement, verify, done
    ↓
[REPORT] Summary + what's ready
    ↓
Repeat
```

---

## I Ask You When

- **Design forks:** "Option A (fast) vs. Option B (robust). Which?"
- **Code ambiguity:** "Spec unclear on X. Assume Y?"
- **Replication edge case:** "Just missed tolerance. Investigate?"
- **Scope question:** "Also refactor Y while here, or focus on X?"

---

## I Just Execute When

- Code fix is obvious (bug, pattern application)
- Verification (tolerance checks, tests, compilation)
- Documentation (logs, commits)
- Plotting (per established standards)
- Deployment (after you approve, I ship automatically)

---

## Quality Gates (No Exceptions)

| Score | Action |
|-------|--------|
| >= 80 | Ready to commit |
| < 80  | Fix blocking issues |

---

## Non-Negotiables

- **Paths:** Relative paths everywhere. STATA: `global projectdir` at top, never `/Users/...`
- **Seed:** `set seed 12345` before any bootstrap or simulation in STATA
- **Figures:** White background, labeled axes, exported as `.pdf` or `.eps`. Okabe-Ito palette mandatory (no red/green combos)
- **Theme:** Dark navy headers (`#003B6F`), black body text — colorblind-safe throughout
- **Replication fidelity:** STATA code must implement exactly what slides describe (same estimator, same SE method, same sample)

---

## Preferences

**Visual:** Polished, publication-ready — no draft-quality output ships
**Reporting:** Structured and precise. High-level summary by default; details available on request.
**Session logs:** Always (post-plan, incremental, end-of-session)
**Replication:** Strict — code must match slides exactly; flag near-misses
**Check-in frequency:** More frequent in early sessions while learning the workflow; reduce as confidence grows

---

## Exploration Mode

For experimental work, use the **Fast-Track** workflow:
- Work in `explorations/` folder
- 60/100 quality threshold (vs. 80/100 for production)
- No plan needed — just a research value check (2 min)
- See `.claude/rules/exploration-fast-track.md`

---

## Next Step

You provide task → I plan (if needed) → Your approval → Execute → Done.
