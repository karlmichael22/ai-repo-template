# Implementation Plan — {PR-ID}: {Title}

> Created by the Execution Engineer.
> Requires Lead Engineer approval before any implementation.
> Place in `/ops/plans/`.
> See `/ops/TURN_PROTOCOL.md` for workflow rules.

This plan defines **how the PR spec will be executed**, not why it exists.

---

## 1) Spec Reference

- PR Spec: `/ops/pr_queue/{PR-ID}.md`
- PR Classification: {copied from PR spec}

---

## 2) Grounding Confirmation (required)

The following authoritative documents have been ingested silently:

- [ ] PRODUCT_CONTRACT.md
- [ ] SPEC.md
- [ ] DECISIONS.md
- [ ] ROADMAP.md

Rule:
- These documents are NOT summarized.
- Any conflict discovered during execution requires STOP + escalation.

---

## 3) Authority References (from PR spec)

List the exact docs + section headers or IDs that govern this plan.
These MUST match the PR spec.

- {doc} → {section / ID}
- …

If additional authority seems required:
→ STOP and request PR spec update.

---

## 4) Reads (minimal set — required)

List the **exact files and sections** that will be read before implementation.
No broad repo scans allowed.

Format:
- `{path}` → {section / reason}

If more reads become necessary during execution:
→ STOP and escalate.

---

## 5) Writes (expected touch list — required)

List the **exact files expected to change**.

Format:
- `{path}` → {type of change}

If additional files must be modified:
→ STOP and escalate.

---

## 6) Execution Steps (ordered, bounded)

List concrete, sequential steps.
Each step must be justified by an Authority Reference or Acceptance Test ID.

1. {Step} — (ref: G-xx / R-xx / F-xx / AT-xx)
2. {Step} — (ref: …)

No speculative or exploratory steps.

---

## 7) Edge Cases / Failure Modes

List known edge cases or failure modes relevant to this PR.
Each should reference an existing failure mode, rule, or test if applicable.

- {Case} — {handling or reference}

---

## 8) Tests

List exact tests to run.

- {command or placeholder}
- Expected test count change: {+N / no change}

If tests are missing or unclear:
→ STOP and request clarification.

---

## 9) Doc Impact

Explicitly state ONE of the following:

A) Docs to update:
- `{file}` → {section / ID}

OR

B) Explicit confirmation:
> "Confirmed: No behavioral contract changes."

Silence is not allowed.

---

## 10) Out of Scope (re-confirmation)

Restate what this plan intentionally does NOT cover,
to prevent scope creep during implementation.

- …
- …

---

## 11) STOP Conditions (non-negotiable)

Implementation MUST STOP if any of the following occur:

- Missing or ambiguous Authority References
- Conflict with PRODUCT_CONTRACT or SPEC
- Need to read files not listed in "Reads"
- Need to modify files not listed in "Writes"
- Undocumented behavioral change
- New decision required without DECISIONS entry

---

## Approval Gate

This plan requires explicit Lead Engineer approval before implementation.

No code may be written until approved.
