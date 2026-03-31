# {Project Name}

## What Is This?

This is a **repo template for AI-assisted product development**. It uses two AI agents — a Lead Engineer and an Execution Engineer — to build your product from a simple product brief.

You provide the idea. The agents handle specs, planning, implementation, and review — with you approving at each step.

---

## Prerequisites

You need an AI-powered code editor that supports multi-file editing and inline chat. Any of the following will work:

- **VS Code** + [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (CLI or extension)
- **Cursor**
- **Windsurf**
- **OpenAI Codex** (or any agent that can read/write project files)

The key requirement is that the AI can read and edit files across the repo. The workflow uses two separate chat sessions (one per agent), so your editor needs to support running at least two independent AI conversations against the same project.

---

## Quick Start

### 1. Copy and rename this folder
Duplicate this `repo-template` folder and rename it to your project (e.g., `my-app`). Initialize a git repo if one doesn't exist.

### 2. Paste your product brief
Open `product-brief.md` and replace the placeholder with your product idea. Write as much or as little as you want — the AI will ask clarifying questions.

### 3. Open in your editor
Open your new project folder in your code editor.

### 4. Run the bootstrap
Start a new AI chat session and send this prompt:

```
Read @ops/BOOTSTRAP.md and follow its instructions.
```

This tells the AI to read the bootstrap script and execute it. The AI will:
- Read your product brief
- Ask you clarifying questions
- Generate a full spec pack
- Populate all project documentation
- Leave the repo ready for development

### 5. Start building
Once the bootstrap is complete, ask the Lead Engineer to review the roadmap and write the first PR spec. This kicks off the two-agent workflow:

```
Ground as Lead Engineer (@ops/ROLE_LE.md). Review the roadmap and write the first PR spec.
```

From here, every change follows the cycle: **Spec → Plan → Approve → Implement → Review → Merge**

---

## The Two-Agent Workflow

This template uses two AI agents that alternate control. You run them in **two separate chat sessions** (e.g., two terminal panes, two Cursor chats, two Claude Code sessions) against the same project folder.

### The agents

| Agent | Role | You are... |
|-------|------|------------|
| **Lead Engineer** | Writes specs, reviews plans, approves/rejects work, guards correctness | The product owner collaborating with this agent |
| **Execution Engineer** | Creates implementation plans, writes code, produces merge receipts | Hands-off — this agent executes autonomously |

### How they communicate

The agents don't talk to each other directly. They coordinate through **files in the `ops/` folder**:

- `ops/STATE.md` — the single source of truth for what's happening and whose turn it is
- `ops/pr_queue/` — PR specs written by the Lead Engineer
- `ops/plans/` — implementation plans and approvals
- `ops/receipts/` — merge receipts from the Execution Engineer

Each agent reads `STATE.md` to figure out what stage the workflow is in and what it should do next.

### The workflow cycle

| Step | Agent | What happens |
|------|-------|-------------|
| 1. Spec | Lead Engineer | Writes a PR spec defining what to build and why |
| 2. Plan | Execution Engineer | Creates an implementation plan (no code yet) |
| 3. Approve | Lead Engineer | Reviews the plan, approves or requests changes |
| 4. Implement | Execution Engineer | Builds it according to the approved plan |
| 5. Review | Lead Engineer | Reviews the implementation |
| 6. Merge | Lead Engineer | Merges the work |

### Running it in practice

1. **Lead Engineer session** — start a chat and ground it with: `Ground as Lead Engineer (@ops/ROLE_LE.md)`
2. **Execution Engineer session** — start a separate chat and ground it with: `Ground as Execution Engineer (@ops/ROLE_EE.md)`
3. Work alternates between sessions. Check `ops/STATE.md` to see whose turn it is.
4. When one agent finishes its stage, switch to the other session and tell it to pick up where things left off.

You stay in the loop the entire time — the Lead Engineer won't approve anything without your sign-off.

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
| `CLAUDE.md` | Agent grounding file (re-read after context resets) |
