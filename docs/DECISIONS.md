# Decisions

> **Status:** Active
> **Date:** {date}
> **Owner:** Product
> **Change control:** New entries require Lead Engineer review. Entries are append-only; superseded decisions are marked as such with a pointer to the replacement.

This document is part of the **Project Truth Set (PTS)** and must be ingested silently after compaction.

---

## Purpose

This document records architectural and product decisions, their context, alternatives considered, and consequences. It is the authoritative "why we chose this" layer.

Product decisions come only from the Spec Pack or later PRs.

---

## Format

Each entry follows:

```
### OD-xx: [Title]
- **Status:** Locked | OPEN (not locked)
- **Date:** YYYY-MM-DD
- **Context:** Why this decision was needed
- **Decision:** What was decided
- **Alternatives:** What else was considered
- **Consequences:** What follows from this decision
```

---

## Decision Log

### PR00: Established documentation system
- **Status:** Locked
- **Date:** {date}
- **Context:** Need a canonical set of docs to govern the build.
- **Decision:** Adopted PTS (Project Truth Set) with PRODUCT_CONTRACT, SPEC, DECISIONS, ROADMAP.
- **Alternatives:** Wiki-based docs; inline code comments only.
- **Consequences:** All decisions and contracts are version-controlled alongside code.
