# Turn Protocol

> This document defines the enforced workflow for all PRs in this repository.
> All agents and humans MUST follow this protocol without exception.

---

## Workflow Stages

1. **PR Spec Creation** (Lead Engineer)
   - Write PR spec → `ops/pr_queue/{PR-ID}.md`
   - Update STATE.md → stage: PLAN_PENDING, owner: Execution Engineer

2. **Implementation Plan Creation** (Execution Engineer — NO code)
   - Write plan → `ops/plans/{PR-ID}.plan.md`
   - Update STATE.md → stage: PLAN_REVIEW, owner: Lead Engineer

3. **Plan Review & Approval** (Lead Engineer)
   - Write approval → `ops/plans/{PR-ID}.approval.md`
   - Update STATE.md → stage: IMPLEMENTATION_IN_PROGRESS, owner: Execution Engineer

4. **Implementation** (Execution Engineer — after approval only)
   - Execute plan as approved
   - Write receipt → `ops/receipts/{PR-ID}.receipt.md`
   - Update ROADMAP.md
   - Update STATE.md → stage: READY_FOR_REVIEW, owner: Lead Engineer

5. **Review** (Lead Engineer)
   - Review receipt, verify acceptance criteria met
   - If approved: Update STATE.md → stage: READY_TO_MERGE, owner: Lead Engineer
   - If issues found: Update STATE.md → back to IMPLEMENTATION_IN_PROGRESS with blocking note

6. **Human Merge Gate** (Lead Engineer)
   - Execute merge
   - Update STATE.md → stage: MERGED or IDLE

---

## Canonical Stage Names

| Stage | Meaning |
|---|---|
| `IDLE` | No active PR |
| `SPEC_PENDING` | PR spec being written |
| `PLAN_PENDING` | Spec written, plan not yet created |
| `PLAN_REVIEW` | Plan awaiting approval |
| `IMPLEMENTATION_IN_PROGRESS` | Approved plan being executed |
| `READY_FOR_REVIEW` | Implementation complete, receipt written |
| `READY_TO_MERGE` | Review approved, ready for merge |
| `MERGED` | Merged, roadmap updated |

---

## Stage Artifacts (Mandatory)

After completing ANY workflow stage transition, you MUST write the corresponding artifact and update `/ops/STATE.md` immediately. Do not defer this.

| Stage | Artifact | Location |
|-------|----------|----------|
| 1 — Spec | PR spec | `ops/pr_queue/{PR-ID}.md` |
| 2 — Plan | Implementation plan | `ops/plans/{PR-ID}.plan.md` |
| 3 — Approval | Plan approval | `ops/plans/{PR-ID}.approval.md` |
| 5 — Receipt | Merge receipt | `ops/receipts/{PR-ID}.receipt.md` |

---

## Non-Negotiable Rules

- **No code changes before explicit plan approval.** PR00 is the only exception (initial scaffolding).
- **Stage artifacts are mandatory.** No stage transition is complete without its artifact.
- **STOP on ambiguity.** If a requirement is unclear, halt and escalate — do not guess.
- **Bounded reads.** Agents read ONLY the files listed in "Authority References" (PR spec) or "Reads" (plan). No broad repo scans.
- **Post-compaction re-grounding.** After compaction, re-ground from PTS silently. Do not write sync summaries.
- **Approval threshold.** Prefer "approve with binding conditions" over "changes required" when issues are addressable during implementation without re-planning. Reserve "changes required" for structural problems that require the plan to be rewritten.

---

## Project Semantics Note

Project-specific semantics are introduced only via Spec Pack–driven PRs (e.g., PR01). This protocol governs workflow mechanics, not product behavior.

---

## Two-Pane Workflow

After PR01 seeds the docs, open two Claude Code panes:

- **Lead Engineer pane:** Reference `@ops/ROLE_LE.md`
- **Execution Engineer pane:** Reference `@ops/ROLE_EE.md`

Each pane operates independently within its stage responsibilities.
