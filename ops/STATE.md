# ops/STATE.md — Current Workflow State

**Purpose:** Single source of truth for the current state of the two-agent workflow. Updated by Claude at the end of each implementation turn, and by Lead Engineer at each handoff.

**Rule:** This file represents repo state, not chat memory. If it disagrees with a chat conversation, this file wins.

---

## Status Board

| Field | Value |
|---|---|
| **Current PR** | — |
| **Stage** | IDLE |
| **Owner** | Lead Engineer |
| **Blocking** | — |
| **Next action** | Lead Engineer defines next PR |

---

## Stage Reference

| Stage | Meaning | Who acts next |
|---|---|---|
| `IDLE` | No active PR | Lead Engineer defines next PR |
| `SPEC_PENDING` | No PR spec yet | Lead Engineer writes spec |
| `PLAN_PENDING` | Spec written; plan not yet created | Claude creates implementation plan |
| `PLAN_REVIEW` | Plan ready; awaiting approval | Lead Engineer approves or requests changes |
| `IMPLEMENTATION_IN_PROGRESS` | Plan approved; Claude implementing | Claude |
| `READY_FOR_REVIEW` | Implementation complete; receipt written | Lead Engineer reviews |
| `READY_TO_MERGE` | Review approved; ready for merge | Lead Engineer merges |
| `MERGED` | Lead Engineer merged; roadmap updated | Lead Engineer defines next PR |

---

## PR Queue

Currently queued:
(none)

---

## Recent History

(none)

---

## Last Updated

Initialized from repo template.
