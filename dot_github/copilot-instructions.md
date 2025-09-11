# Copilot Instructions — PDD + MCP

Operate with Prompt‑Driven Development (PDD) and MCP-first behavior. Default flow: Ideate → Plan → Execute → Document. For small, rapid tasks, switch to the Concise chat mode.

## Mode Decision (When to use which)
- Use "Concise" for: grooming, clarifying scope, small/surgical changes, executing a single plan task.
- Use "Plan" for: generating or updating the plan from ideation; read-only analysis, ordering, and risk assessment.
- Use "Research" for: exploring technologies or gathering information with citations; read-first, no code edits.
- Use default chat with prompt files for: broader tasks outside PDD phases.

## Global Behavior
- MCP-first: use SequentialThinking (stepwise), Memory (persistence), GitHub (repo context/issues/PRs).
- Traceability: record assumptions, decisions, and artifact paths in outputs; prefer facts from repo/GitHub over guesses.
- One primary artifact per phase run; keep everything under `pdd/` using the required filenames.
- Safety: if asked for harmful/forbidden content, reply: "Sorry, I can't assist with that."

## Concise Chat Mode
Activate via mode picker or by referencing `.github/chatmodes/concise.chatmode.md` (name: "Concise").
- ≤ 10 lines per reply; next action first.
- Refine requests to 3–7 TODOs; exactly one in-progress at a time.
- Concrete outputs with exact paths; validation per item: PASS/FAIL + next.
- Minimal reply template:
  - Objective + next action (1 line)
  - TODOs (one in-progress)
  - Execution notes (1–3 bullets)
  - Validation: PASS/FAIL (+ next)
  - Links/paths changed

## Plan Chat Mode
Activate via mode picker or by referencing `.github/chatmodes/plan.chatmode.md` (name: "Plan").
- Read-first; no code edits. Convert ideation → plan with a WBS and ordering.
- Output one plan at `pdd/plan/YYYY-MM-DD-<slug>-plan.md`; keep responses ≤ 16 lines and link to the plan.

## Research Chat Mode
Activate via mode picker or by referencing `.github/chatmodes/research.chatmode.md` (name: "Research").
- Research-first; no code edits. Cite sources; synthesize findings into actionable steps aligned to PDD.
- Keep replies ≤ 20 lines; link to sources and notes.

## Phase Prompts (run when needed)
- Ideate: `pdd/prompts/ideate.prompt.md` → write `pdd/ideate/YYYY-MM-DD-<slug>.md`.
- Plan: `pdd/prompts/plan.prompt.md` → write `pdd/plan/YYYY-MM-DD-<slug>-plan.md`.
- Execute: `pdd/prompts/execute.prompt.md` → update plan; create `pdd/execute/T-XXX-<slug>/README.md`.
- Document: `pdd/prompts/document.prompt.md` → update plan; emit `pdd/execute/documentation-summary-YYYY-MM-DD.md`.

## File/Folder Conventions
- Ideation: `pdd/ideate/YYYY-MM-DD-<slug>.md`
- Plan: `pdd/plan/YYYY-MM-DD-<slug>-plan.md`
- Execute (per task): `pdd/execute/T-XXX-<slug>/README.md`
- Doc summary: `pdd/execute/documentation-summary-YYYY-MM-DD.md`
- Use kebab-case `<slug>`, zero-padded task ids (`T-001`), ISO dates.

## Execution Rules
- Choose the next eligible plan task (`status: not-started`, deps done). If blocked, mark `blocked` with reason and pick the next.
- For each task: include acceptance criteria and verification steps; keep steps small (30–120 min).
- Quality gates (when applicable): build, lint/typecheck, unit tests, smoke test.

## Validation Commands (adjust to project)
- Build:
  ```bash
  npm run build
  ```
- Lint/Typecheck:
  ```bash
  npm run lint
  npm run typecheck
  ```
- Tests:
  ```bash
  npm test -- --watch=false
  ```

## Quick Starters
- Ideate: "Use `pdd/prompts/ideate.prompt.md` to produce the ideation artifact for <initiative>."
- Plan: "Switch to Plan and convert the latest ideation artifact into a plan file per the template."
- Execute: "Switch to Concise and execute the next eligible plan task; update artifacts and plan."
- Document: "Use `pdd/prompts/document.prompt.md` to reconcile plan vs execution and produce the summary."
- Research: "Switch to Research and summarize options with citations; propose next steps aligned to PDD."
- Concise mode: "Switch to Concise and refine this request; execute the first todo."
