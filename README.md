# Design Thinking Prompt‑Driven Development (PDD) — Workspace Guide

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

This project is licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0). See the `LICENSE` file for details.

> Design Thinking Cheat Sheet
- Switch to design thinking modes: Chat view → Mode → pick "Ideate" | "Plan" | "Execute" | "Document"
- Quick modes: "Concise" for rapid execution | "Research" for citations and synthesis
- Design thinking workflow: "Switch to Ideate and explore user needs" → "Switch to Plan for learning experiments" → "Switch to Execute for prototyping" → "Switch to Document for synthesis"

This repository includes a Design Thinking Prompt‑Driven Development (PDD) workflow with human-in-the-loop brainstorm-dev sessions powered by MCP and custom chatmodes. Use this README to run **Ideate → Plan → Execute → Document** with consistent, user-centered, repeatable steps.

## What’s Included
- Design thinking chatmodes for human-in-the-loop brainstorm-dev sessions
  - `dot_github/chatmodes/ideate.chatmode.md` — user-centered problem exploration and solution concepts
  - `dot_github/chatmodes/plan.chatmode.md` — prototyping-focused planning for learning experiments
  - `dot_github/chatmodes/execute.chatmode.md` — experimentation and rapid prototyping
  - `dot_github/chatmodes/document.chatmode.md` — learning synthesis across design thinking sessions
- Specialized workflow chatmodes
  - `dot_github/chatmodes/concise.chatmode.md` — concise, precise execution mode
  - `dot_github/chatmodes/research.chatmode.md` — research/citations mode
- Supporting prompts for structured tasks
  - `dot_github/prompts/execute.prompt.md`
  - `dot_github/prompts/document.prompt.md`
- Global Copilot instructions
  - `.github/copilot-instructions.md` — MCP-first behavior, file conventions, and quick starters

IMPORTANT: This repository currently stores GitHub-specific files under a folder named `dot_github/` to avoid accidental activation. To enable GitHub features (workflows, issue templates, CODEOWNERS, chat modes), rename the `dot_github/` folder to `.github/` in your local copy and push the change to your fork or repository root. Example:

  mv dot_github .github
  git add -A
  git commit -m "chore: enable GitHub features by renaming dot_github to .github"
  git push origin main

## Prerequisites
- VS Code with GitHub Copilot Chat enabled
- (Optional) MCP servers configured for:
  - SequentialThinking (stepwise reasoning)
  - Memory (persistent context)
  - GitHub (issues/PRs/repo context)

## Folder Map
- `pdd/prompts/` — prompt files you can run in chat
- `pdd/ideate/` — ideation artifacts (`YYYY-MM-DD-<slug>.md`)
- `pdd/plan/` — plans (`YYYY-MM-DD-<slug>-plan.md`)
- `pdd/execute/` — per-task outputs (`T-XXX-<slug>/README.md`)
- `pdd/.github/chatmodes/` — chat modes (`*.chatmode.md`)
- `pdd/.github/copilot-instructions.md` — global operating instructions

## Quick Start
1) Ideate (produce a concept brief)
   - Chat: “Switch to Ideate and explore user needs for <problem>.”
   - Output: `pdd/ideate/YYYY-MM-DD-<slug>.md`
2) Plan (convert ideation → executable plan)
   - Mode: Switch to Plan (or reference `.github/chatmodes/plan.chatmode.md`)
   - Chat: “Switch to Plan and convert ideation into learning experiments.”
   - Output: `pdd/plan/YYYY-MM-DD-<slug>-plan.md`
3) Execute (task-by-task)
   - Mode: Switch to Concise
   - Chat: “Switch to Execute and run the next prototype experiment.”
   - Output: `pdd/execute/T-XXX-<slug>/README.md` + plan updates
4) Document (reconcile and summarize)
   - Chat: “Switch to Document and synthesize session insights.”
   - Output: `pdd/execute/documentation-summary-YYYY-MM-DD.md` + updated plan

## Chat Modes
### Concise (execution-focused)
- File: `.github/chatmodes/concise.chatmode.md`
- Use when: grooming, clarifying scope, executing single tasks, making small changes
- Behavior: ≤ 10 lines, next action first, 3–7 TODOs with one in-progress, concrete paths, PASS/FAIL validation
- Starter: “Switch to Concise and refine this request; execute the first todo.”

### Plan (read-first planning)
- File: `.github/chatmodes/plan.chatmode.md`
- Use when: converting ideation into a plan; ordering, risks, WBS; no code edits
- Behavior: single plan output, tasks sized 30–120 min, critical path and risks, optional GitHub scaffolding
- Starter: “Switch to Plan and convert the latest ideation artifact into a plan file per the template.”

### Research (citations + synthesis)
- File: `.github/chatmodes/research.chatmode.md`
- Use when: exploring tech or gathering information with citations; read-first
- Behavior: 3–6 sources, 5–10 key findings, 3–7 actionable next steps
- Starter: “Switch to Research and summarize options with citations; propose next steps aligned to PDD.”

## Prompts (Supporting Files)
- Execute: `dot_github/prompts/execute.prompt.md`
  - Produces: per-task artifacts under `pdd/execute/T-XXX-<slug>/` and updates plan statuses
  - Verifies: acceptance criteria + quality gates (build/lint/tests)
- Document: `dot_github/prompts/document.prompt.md`
  - Produces: `pdd/execute/documentation-summary-YYYY-MM-DD.md` + updated plan linking artifacts

## File Conventions
- Ideation: `pdd/ideate/YYYY-MM-DD-<slug>.md`
- Plan: `pdd/plan/YYYY-MM-DD-<slug>-plan.md`
- Execute (per task): `pdd/execute/T-XXX-<slug>/README.md`
- Doc summary: `pdd/execute/documentation-summary-YYYY-MM-DD.md`
- Slugs: kebab-case; Tasks: zero-padded (`T-001`); Dates: ISO

## MCP Usage (Always)
- Use SequentialThinking to structure reasoning; keep steps visible/concise.
- Persist decisions and artifact paths to Memory.
- Use GitHub for repo context and to propose issues/labels/milestones when relevant.

## Example Runs
- Start Concise for a small change:
  - “Switch to Concise and refine this request; execute the first todo.”
- Generate Plan from Ideation:
  - “Switch to Plan and convert the latest ideation artifact into a plan file per the template.”
- Research options:
  - “Switch to Research and summarize options with citations; propose next steps aligned to PDD.”

## Troubleshooting
- Mode not found in the picker?
  - Ensure the file exists under `pdd/.github/chatmodes/*.chatmode.md` and reload VS Code.
- Duplicate artifacts?
  - Keep one primary artifact per phase run; clean up or archive old drafts.
- Tooling not applicable?
  - Adjust validation commands (build/lint/tests) to your project; keep acceptance criteria explicit.

---
For global guardrails and quick starters, see `.github/copilot-instructions.md`.
