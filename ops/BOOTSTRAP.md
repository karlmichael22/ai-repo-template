# Bootstrap — Product Brief → Working Repo

> **When to use:** You have a new repo created from the repo template and a product brief pasted into `product-brief.md`.
> **Where to run:** Claude Code, in the new repo's root directory.
> **Output:** Spec Pack generated, all docs seeded, repo ready for PR02+.

---

You are Claude Code running a **one-shot bootstrap** for a new project repository.

The repo template has already created the scaffolding (docs stubs, ops structure, role files, templates). Your job is to:

1. Read the product brief
2. Ask clarifying questions (if needed)
3. Generate a Spec Pack
4. Seed all docs from the Spec Pack
5. Leave the repo ready to work

You MUST follow all steps in order. Do not skip the clarifying questions step.

---

## Step 1 — Read the Product Brief

Read `product-brief.md` in the repo root. This is the sole input for the bootstrap.

If `product-brief.md` is missing or still contains the placeholder text, STOP and tell the user to paste their product brief first.

---

## Step 2 — Clarifying Questions

Before generating the Spec Pack, identify any ambiguities or gaps in the brief. Ask the user **up to 10 clarifying questions** covering:

- Target user / persona gaps
- Core loop ambiguities (what triggers what?)
- Missing business rules or constraints
- Unclear scope boundaries (what's MVP vs deferred?)
- Data model questions (what entities, what relationships?)
- Integration points (external services, APIs?)

Present all questions at once. Wait for the user's answers before proceeding.

If the brief is exceptionally clear and complete, you may proceed with fewer questions, but you MUST ask at least 3.

---

## Step 3 — Generate Spec Pack

Using the product brief + clarifying answers, generate a complete Spec Pack and save it to `ops/spec_pack/SPEC_PACK_v1.md`.

The Spec Pack MUST include all of the following sections (in this order):

### A) Executive Summary (max 10 lines)
- One-sentence value contract
- The Non-Negotiable Use Case (NUC)
- The "Nope list" (top 5 explicit non-goals)
- The 3 highest-risk ambiguities (if any)

### B) Value Contract (1–3 sentences)

### C) Target User (explicit)

### D) Core Loop (Capture → … → Close) with inputs/outputs per step

### E) Visibility Model (what is visible by default vs hidden/collapsed)

### F) Locked MVP Decisions (OD-xx)

### G) Open Decisions Register (OD-xx) — only if anything remains UNSPECIFIED
For each: Status, Context, Options (2–4) + tradeoffs, Recommended MVP default, What would lock it.

### H) MVP Scope (Phase 1) + Phase 2 explicitly deferred

### I) Deterministic Semantics — Rules / invariants / what must never happen (MUST/MUST NOT language)

### J) Failure Modes — User-visible behaviors; at least 10. Include detection/mitigation notes.

### K) Acceptance Tests (AT-01…) — 15–25 Given/When/Then tests

### L) Instrumentation Spec (EV-01…) — 12–20 events with event_name, trigger point, required properties, privacy note.

### M) Stage Gates (Stage 0–3) — Pass/fail criteria per stage.

### N) Traceability Matrix (minimum top 10 items) — OD-xx → (G-xx / INV-xx / R-xx / F-xx) → AT-xx → EV-xx

### O) Product Rails Anchors — UX anchors, Activation anchors, Privacy anchors, Design anchors, GTM anchors.

### Rules for Spec Pack generation:
- Do not write marketing copy. Write implementation-grade contracts.
- Use deterministic language: MUST / MUST NOT / SHALL / SHALL NOT.
- When details are missing, mark UNSPECIFIED and create an OPEN OD entry.
- Use stable IDs: OD-xx, AT-xx, EV-xx, G-xx, INV-xx, R-xx, F-xx.

---

## Step 4 — Seed Docs from Spec Pack

Read each doc template in `/docs/` and populate it from the Spec Pack. Follow this mapping:

| Spec Pack Section | Target File | Target Section |
|-------------------|-------------|----------------|
| Value Contract + Guarantees | `/docs/PRODUCT_CONTRACT.md` | Guarantees (G-xx), Non-goals (NG-xx), Invariants (INV-xx), Failure Modes, Compatibility |
| System Overview + Flows + Rules | `/docs/SPEC.md` | System Overview, Major Flows (F-xx), Rules (R-xx), Boundaries, What Must Never Happen |
| Entity/Schema info | `/docs/DATA_MODEL.md` | Entities, State Machines, Indexing, Migrations, Redaction |
| Locked + Open Decisions | `/docs/DECISIONS.md` | Keep OD-00 from template, add OD-01+ |
| MVP Scope + Phases | `/docs/ROADMAP.md` | Keep PR00/PR01 rows, add planned items |
| Acceptance Tests + Events | `/docs/TESTING.md` | AT-xx tests, EV-xx event spec, test strategy |
| Verification + Debug | `/docs/RUNBOOK.md` | Verification checklist, debug guide, telemetry guidance |
| Data handling + Threats | `/docs/SECURITY.md` | Data handling, sensitive fields, redaction, threats |
| Product Rails Anchors | `/docs/GTM_BRIEF.md` | Create this file if Product Rails exist in Spec Pack |

### Rules for seeding:
- **Map, don't invent.** Every line must trace to the Spec Pack.
- **Preserve doc structure.** Keep headers, status lines, change-control rules, and PTS notes from the template. Only populate content sections.
- **ID consistency.** Use exact IDs from the Spec Pack. Do not renumber.
- **Open Decisions stay open.** OPEN in Spec Pack → OPEN in DECISIONS.md.
- **Update status lines:** `Status: Active`, `Last updated: {today}`, `Owner: Lead Engineer`.
- If the Spec Pack doesn't cover a section, leave the template placeholder and note: "Not covered in Spec Pack — remains placeholder."

---

## Step 5 — Finalize

1. Update `/docs/ROADMAP.md`:
   - PR00 (Docs Bootstrap) → Shipped
   - PR01 (Seed Docs from Spec Pack) → Shipped
   - Add MVP Build and other planned items from the Spec Pack

2. Update `/ops/STATE.md`:
   - Current PR: —
   - Stage: IDLE
   - Owner: Lead Engineer
   - Next action: Lead Engineer defines next PR

3. Update Recent History in STATE.md:
   - `**PR01** — merged ({today}) — Seed Docs from Spec Pack.`
   - `**PR00** — merged ({today}) — Docs Bootstrap (template).`

4. Verify the README.md Docs Index links are correct for all created docs.

---

## Output

After completing all steps, report:

1. Clarifying questions asked and answers received
2. Spec Pack saved to: `ops/spec_pack/SPEC_PACK_v1.md`
3. Files populated (list with source Spec Pack section)
4. Files left as placeholder (with reason)
5. Decisions added (OD-xx list with LOCKED/OPEN status)
6. GTM_BRIEF created: Yes/No
7. STATE.md final state
8. Confirmation: "Bootstrap complete. Repo is ready for PR02+."

---

## STOP Conditions

- `product-brief.md` missing or placeholder → STOP, ask user to paste brief
- Spec Pack section missing for a Tier 0 doc → leave placeholder, note the gap
- ID collision → STOP, escalate
- Brief contradicts itself → STOP, ask user to clarify
- Any uncertainty about a business rule → ask, don't guess
