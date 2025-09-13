# Copilot Instructions — PDD Workspace (Dev Source)

Purpose: This repo is the source for developing PDD chat modes and prompts to be reused in other projects. Do NOT activate them here.

Stance: Keep chat modes and prompts in `dot_github/` (do not rename to `.github/` in this repo). Use a downstream sandbox/project to test activation.

## Design Thinking Chatmodes (author here, activate elsewhere)
- `Ideate`: `dot_github/chatmodes/ideate.chatmode.md` — design thinking ideation with human collaboration
- `Plan`: `dot_github/chatmodes/plan.chatmode.md` — prototyping-focused planning for learning experiments
- `Execute`: `dot_github/chatmodes/execute.chatmode.md` — experimentation and rapid prototyping
- `Document`: `dot_github/chatmodes/document.chatmode.md` — learning synthesis across design thinking sessions
- `Concise`: `dot_github/chatmodes/concise.chatmode.md` — ≤ 10 lines; next action first
- `Research`: `dot_github/chatmodes/research.chatmode.md` — citations + synthesis → actionable steps

## Design Thinking Workflow → Artifacts (in consumer repos)
Use chatmodes directly for design thinking workflow:
- **Ideate chatmode** → `ideate/YYYY-MM-DD-<slug>.md` (user-centered concepts)
- **Plan chatmode** → `plan/YYYY-MM-DD-<slug>-plan.md` (learning experiments)
- **Execute chatmode** → `execute/T-XXX-<slug>/README.md` (experiment results)
- **Document chatmode** → `execute/brainstorm-dev-session-YYYY-MM-DD.md` (session synthesis)

Additional prompts for structured work:
- Execute: `dot_github/prompts/execute.prompt.md` → `execute/T-XXX-<slug>/README.md`
- Document: `dot_github/prompts/document.prompt.md` → `execute/documentation-summary-YYYY-MM-DD.md`

Conventions: kebab‑case slugs, zero‑padded tasks (`T-001`), ISO dates; one primary artifact per phase run; link related artifacts.

## Global behavior
- MCP‑first: use SequentialThinking, Memory (persist decisions + artifact paths), and GitHub (issues/PRs/repo context).
- Traceability: state assumptions, decisions, and exact file paths in outputs.
- Safety: if a request is harmful/forbidden → "Sorry, I can't assist with that."

## Repo structure (essentials)
- `dot_github/prompts/`, `dot_github/chatmodes/` — authoring sources (keep under `dot_github/` here)
- `ideate/`, `plan/`, `execute/` — example artifact roots (for samples, not activated here)
- `.github/copilot-instructions.md` — this file (canonical, active)
- `templates/COPYRIGHT_HEADER.txt` — attribution header (see `CONTRIBUTING.md`)

## Contributor workflow (develop here)
- Add/modify prompts in `dot_github/prompts/` and chat modes in `dot_github/chatmodes/`.
- Keep examples minimal and include concrete paths in guidance.
- Do not rename `dot_github/` in this repo; test activation in a separate sandbox/project.

## Consumer integration (activate in target repo)
1) Copy `dot_github/` into the consumer repo and rename to `.github/`.
2) Commit `.github/chatmodes/*`, `.github/prompts/*`, and `.github/copilot-instructions.md`.
3) Adjust quality gates to the consumer’s build/lint/test commands.

Example (in consumer repo):
```bash
cp -r /path/to/pdd/dot_github ./.github
git add .github && git commit -m "chore: enable PDD chat modes and prompts"
```

## Concrete patterns (for consumers)
- Execute folder: `execute/T-012-improve-docs/README.md` with steps, commands, links to PRs/issues.
- Plan file: `plan/2025-09-13-pdd-rollout-plan.md` with `id`, `deps`, `effort`, `acceptance`, `verification`.
- Document run: `execute/documentation-summary-2025-09-13.md` linking all `T-XXX-*` folders.

## Quick starters
- Design thinking ideation: "Switch to Ideate and explore user needs for <problem>"
- Prototyping planning: "Switch to Plan and convert ideation into learning experiments"
- Experimentation: "Switch to Execute and run the next prototype experiment"
- Learning synthesis: "Switch to Document and synthesize session insights"
- Authoring (here): "Update `dot_github/chatmodes/<mode>.chatmode.md` with clearer guidance"
- Consumer (there): "Switch to Concise and execute the next eligible plan task; update artifacts and plan"

## Attribution & licensing
- This repo is CC BY 4.0. Include attribution as described in `CONTRIBUTING.md`.
- Use `templates/COPYRIGHT_HEADER.txt` when adding files that should carry a header.

Maintainers: keep `.github/` as source of truth; if mirroring `dot_github/`, do so deliberately. In downstream code repos, replace validation with that repo’s build/lint/test commands.
