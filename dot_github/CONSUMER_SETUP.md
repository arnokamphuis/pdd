# Enable PDD Chat Modes & Prompts (Consumer Checklist)

Use this checklist to activate the assets from this repo in your target project.

Prereqs
- VS Code with GitHub Copilot Chat enabled
- Optional: MCP servers for SequentialThinking, Memory, and GitHub

Steps
1) Copy the folder from the source repo:
   - `cp -r /path/to/pdd/dot_github ./.github`
2) Commit the files in your repo:
   - `.github/chatmodes/*`, `.github/prompts/*`
   - If not present, add `.github/copilot-instructions.md` (copy from the source repo's `.github/`)
3) Reload VS Code, open Copilot Chat, and switch to the desired mode (`Concise`, `Plan`, `Research`).
4) Run a phase prompt and validate outputs land in expected paths:
   - Ideate → `ideate/YYYY-MM-DD-<slug>.md`
   - Plan → `plan/YYYY-MM-DD-<slug>-plan.md`
   - Execute → `execute/T-XXX-<slug>/README.md`
   - Document → `execute/documentation-summary-YYYY-MM-DD.md`
5) Tailor quality gates to your project (build/lint/test commands) and update `.github/copilot-instructions.md` accordingly.

Conventions
- Slugs: kebab‑case; Task IDs: zero‑padded (`T-001`); Dates: ISO
- One primary artifact per phase run; link related artifacts

Troubleshooting
- Modes not available?
  - Ensure the folder is named `.github/` at the repository root and reload VS Code.
- Artifacts not created under the right folders?
  - Confirm the prompts reference the correct relative paths and your repo allows writing to them.
- Need to adapt commands?
  - Replace validation/build/lint steps in `.github/copilot-instructions.md` with your project’s actual commands.
