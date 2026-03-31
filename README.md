# {Project Name}

## What Is This?

This is a **repo template for AI-assisted product development**. It uses two AI agents (a Lead Engineer and an Execution Engineer) running in VS Code to build your product from a simple product brief.

You provide the idea. The agents handle specs, planning, implementation, and review — with you approving at each step.

---

## Quick Start

### 1. Copy and rename this folder
Duplicate this `repo-template` folder and rename it to your project (e.g., `my-app`).

### 2. Paste your product brief
Open `product-brief.md` and replace the placeholder with your product idea. Write as much or as little as you want — the AI will ask clarifying questions.

### 3. Open in VS Code
Open your new project folder in VS Code.

### 4. Run the bootstrap
Open a terminal in VS Code, start Claude Code (`claude`), and type:

```
ground in @ops/BOOTSTRAP.md
```

Claude will:
- Read your product brief
- Ask you clarifying questions
- Generate a full spec pack
- Set up all project documentation
- Leave the repo ready to work

### 5. Register in the dashboard
Open the command palette (`Ctrl+Shift+P`) and run `Ops: Register Project`, then select your project folder. It will appear on the Ops Control Plane dashboard in the sidebar.

### 6. Start building
Define your first PR. The two-agent workflow handles the rest:

**Lead Engineer** (you + AI) writes specs and reviews
**Execution Engineer** (AI) plans and implements

Every change goes through: **Spec → Plan → Approve → Implement → Review → Merge**

---

## How the Workflow Works

| Step | Who | What happens |
|------|-----|-------------|
| 1. Spec | Lead Engineer | Writes a PR spec defining what to build and why |
| 2. Plan | Execution Engineer | Creates an implementation plan (no code yet) |
| 3. Approve | Lead Engineer | Reviews the plan, approves or requests changes |
| 4. Implement | Execution Engineer | Builds it according to the approved plan |
| 5. Review | Lead Engineer | Reviews the implementation |
| 6. Merge | Lead Engineer | Merges the work |

All state is tracked in `ops/STATE.md`. The dashboard shows progress in real time.

---

## Project Files

### You'll interact with
| File | What it's for |
|------|--------------|
| `product-brief.md` | Your product idea (paste here first) |
| `ops/STATE.md` | Current workflow state (updated automatically) |
| `docs/ROADMAP.md` | What's been built and what's planned |

### Managed by the agents
| Folder | Contents |
|--------|----------|
| `docs/` | Product contracts, specs, decisions, architecture |
| `ops/pr_queue/` | PR specifications |
| `ops/plans/` | Implementation plans and approvals |
| `ops/receipts/` | Merge receipts |
| `ops/spec_pack/` | Generated spec pack from your brief |

### Agent configuration
| File | Purpose |
|------|---------|
| `ops/ROLE_LE.md` | Lead Engineer behavior rules |
| `ops/ROLE_EE.md` | Execution Engineer behavior rules |
| `ops/TURN_PROTOCOL.md` | Workflow stage rules |
| `ops/BOOTSTRAP.md` | One-time setup script |
| `CLAUDE.md` | Auto-generated grounding file (don't edit) |
