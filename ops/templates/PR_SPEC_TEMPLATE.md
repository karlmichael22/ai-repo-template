# PR Spec — {PR-ID}: {Short, Descriptive Title}

> Authoritative PR specification.
> Place this file in `/ops/pr_queue/`.
> See `/ops/TURN_PROTOCOL.md` for the enforced workflow.

This PR spec defines **intent, scope, and authority boundaries**.
Implementation details belong in the implementation plan.

---

## 1) PR Classification (required)

Check all that apply:

- [ ] Runtime behavior / user-facing semantics
- [ ] Deterministic rule / state machine / gating
- [ ] Governance / policy interpretation
- [ ] Schema / persistence / migration
- [ ] Observability / tracing / telemetry
- [ ] UI-only
- [ ] Docs-only
- [ ] Strategic (non-shipped)

If any box above implies behavioral change, corresponding docs MUST be updated.

---

## 2) Goal

One sentence:
> What does this PR accomplish?

Must be outcome-focused, not task-focused.

---

## 3) Non-Goals (explicit)

List what this PR does NOT do.
Anything not listed here is assumed in scope.

- …
- …

---

## 4) Scope (concrete)

Describe exactly what is included.
Be explicit about:
- behaviors
- boundaries
- exclusions
- files or subsystems affected (high level)

Avoid implementation detail.

---

## 5) Project Truth Set (PTS) Acknowledgement

This PR operates under the following authoritative documents:

- `/docs/PRODUCT_CONTRACT.md`
- `/docs/SPEC.md`
- `/docs/DECISIONS.md`
- `/docs/ROADMAP.md`

`/docs/DATA_MODEL.md` applies when schema changes are involved.

Rule:
- These documents are ingested silently.
- They are not summarized in plans or approvals.
- Any conflict requires explicit resolution.

---

## 6) Authority References (required, bounded)

List the **exact** docs + section headers or IDs that govern this PR.

This is the **only** authority the Execution Engineer may rely on
beyond the Project Truth Set.

Example format:
- PRODUCT_CONTRACT.md → Guarantees → G-03
- SPEC.md → Deterministic Rules → R-07
- SPEC.md → Major Flows → F-02
- DECISIONS.md → OD-09

Rules:
- Keep this list minimal (3–7 items).
- If missing or ambiguous, implementation MUST STOP.

---

## 7) Behavioral Impact Assessment

Answer explicitly:

- Does this PR change runtime or user-visible behavior?
  - [ ] Yes
  - [ ] No

If **Yes**, list:
- affected guarantees (G-xx)
- affected rules/flows (R-xx / F-xx)
- required doc updates (file + section)

If **No**, this PR MUST conclude with:
> "Confirmed: No behavioral contract changes."

---

## 8) Required Doc Updates (if any)

List the exact updates required, or state "None".

Format:
- `/docs/SPEC.md` → Section R-07
- `/docs/DECISIONS.md` → New entry OD-12
- `/docs/DATA_MODEL.md` → Entity XYZ

Silence is not allowed.

---

## 9) Acceptance Criteria

List objective pass/fail criteria.
These should map cleanly to AT-xx tests where applicable.

- [ ] …
- [ ] …

---

## 10) Constraints & Guardrails

List constraints the Execution Engineer MUST NOT violate, such as:
- invariants
- non-goals
- safety constraints
- privacy constraints

These should reference IDs where possible.

---

## 11) Out of Scope (re-confirmation)

Restate what is intentionally deferred or excluded,
to prevent scope creep during implementation.

---

## 12) Handoff to Execution Engineer

This PR is ready for:

- [ ] Implementation plan creation
- [ ] Clarification required before planning

If clarification is required, list questions explicitly.

---

## Final Note (non-optional)

- This PR spec defines **what and why**.
- The implementation plan defines **how**.
- Any ambiguity not resolved here MUST block execution or trigger a DECISIONS entry.
