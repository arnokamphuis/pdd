# Prompt‑Driven Development (PDD) — Workspace Guide

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

This project is licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0). See the `LICENSE` file for details.

> Cheat Sheet
- Switch mode: Chat view → Mode → pick "Concise" | "Plan" | "Research".
- Run a phase: "Use `pdd/prompts/<phase>.prompt.md` to produce the artifact." (Ideate | Plan | Execute | Document)
- Execute fast (Concise): "Switch to Concise and refine this request; execute the first todo."
- Plan fast (Plan): "Switch to Plan and convert the latest ideation artifact into a plan file per the template."
- Research fast (Research): "Switch to Research and summarize options with citations; propose next steps."

This repository includes a Prompt‑Driven Development (PDD) workflow powered by MCP and custom chat modes. Use this README to run Ideate → Plan → Execute → Document with consistent, repeatable steps.

## What’s Included
- PDD prompts (reusable) for each phase
  - `pdd/prompts/ideate.prompt.md`
  - `pdd/prompts/plan.prompt.md`
  - `pdd/prompts/execute.prompt.md`
  - `pdd/prompts/document.prompt.md`
- Custom chat modes for specialized workflows
  - `.github/chatmodes/concise.chatmode.md` — concise, precise execution mode
  - `.github/chatmodes/plan.chatmode.md` — read-first, plan-only mode
  - `.github/chatmodes/research.chatmode.md` — research/citations mode
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
   - Chat: “Use `pdd/prompts/ideate.prompt.md` to produce the ideation artifact for <initiative>.”
   - Output: `pdd/ideate/YYYY-MM-DD-<slug>.md`
2) Plan (convert ideation → executable plan)
   - Mode: Switch to Plan (or reference `.github/chatmodes/plan.chatmode.md`)
   - Chat: “Convert the latest ideation artifact into a plan per the template.”
   - Output: `pdd/plan/YYYY-MM-DD-<slug>-plan.md`
3) Execute (task-by-task)
   - Mode: Switch to Concise
   - Chat: “Execute the next eligible plan task; update artifacts and plan.”
   - Output: `pdd/execute/T-XXX-<slug>/README.md` + plan updates
4) Document (reconcile and summarize)
   - Chat: “Use `pdd/prompts/document.prompt.md` to reconcile plan vs execution and produce the summary.”
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

## Prompts (Phase Files)
- Ideate: `pdd/prompts/ideate.prompt.md`
  - Produces: `pdd/ideate/YYYY-MM-DD-<slug>.md` (concept brief)
  - Includes: Q&A, options, scoring, rationale, acceptance criteria
- Plan: `pdd/prompts/plan.prompt.md`
  - Produces: `pdd/plan/YYYY-MM-DD-<slug>-plan.md` (deliverables, milestones, WBS, ordering, risks)
  - Tasks: id, owner, deps, effort, acceptance, verification; critical path
- Execute: `pdd/prompts/execute.prompt.md`
  - Produces: per-task artifacts under `pdd/execute/T-XXX-<slug>/` and updates plan statuses
  - Verifies: acceptance criteria + quality gates (build/lint/tests)
- Document: `pdd/prompts/document.prompt.md`
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
