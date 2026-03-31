# Merge Receipt — {PR-ID}: {Title}

> Created after implementation and test execution, before merge.
> Place in `/ops/receipts/`.
> See `/ops/TURN_PROTOCOL.md` for workflow rules.

Receipts are factual, not narrative.
Do NOT summarize contracts/specs.
Reference doc sections/IDs instead of paraphrasing.

---

## 1) Classification (Confirmed)

Check all that apply:

- [ ] Runtime behavior / user-facing semantics
- [ ] Deterministic rule / state machine / gating
- [ ] Governance / policy interpretation
- [ ] Schema / persistence / migration
- [ ] Observability / tracing / telemetry
- [ ] UI-only
- [ ] Docs-only
- [ ] Strategic (non-shipped)

---

## 2) Plan & Approval References

- PR Spec: `/ops/pr_queue/{PR-ID}.md`
- Plan: `/ops/plans/{PR-ID}.plan.md`
- Approval: `/ops/plans/{PR-ID}.approval.md` (if applicable)

---

## 3) Files Changed

### Files Created

| File | Purpose |
|------|---------|
| {path} | {short purpose} |

### Files Modified

| File | Change |
|------|--------|
| {path} | {short, factual change} |

---

## 4) Acceptance Criteria Results

List each AC item from the PR spec and mark pass/fail.

- [x] {AC-1} — pass
- [ ] {AC-2} — fail: {reason} / {follow-up}

---

## 5) Docs Updated (file + section/ID)

List doc updates with section headers or IDs (G-xx / INV-xx / R-xx / F-xx / OD-xx), not summaries.

| Document | Section/ID | Change Type |
|----------|------------|------------|
| {doc} | {ID/section} | {added/modified/removed} |

OR explicitly state:

> "No docs changes required."

Silence is not allowed.

---

## 6) Tests Run (exact)

- {command}
- {command}

Results:
- Total tests: {N} (or "unknown" if framework not instrumented)
- New/changed tests: {+N / no change}
- All passing: {Yes/No}
- Migrations: {N} (unchanged / +N)

---

## 7) Behavioral Contract Confirmation

Choose ONE and be explicit:

A) No behavioral change:
> "Confirmed: No behavioral contract changes."

B) Behavioral change occurred (must be documented above):
- Affected: {G-xx / INV-xx / R-xx / F-xx}
- Docs updated: {file + section/ID}

---

## 8) Mismatches / Risks (if any)

List any mismatch detected between:
- PR spec ↔ plan
- plan ↔ implementation
- docs ↔ code
- approval conditions ↔ delivered result

If none, state:
> "No blocking mismatches detected."

---

## 9) Workflow State Updates

- `/ops/STATE.md` updated to: {READY_FOR_REVIEW / READY_TO_MERGE}
- `/docs/ROADMAP.md` updated: {Yes/No} (only if shipped/merged)

(If not updated, state why.)
