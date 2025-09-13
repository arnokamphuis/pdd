# Enable Design Thinking PDD Chatmodes (Consumer Checklist)

Use this checklist to activate the design thinking chatmodes and prompts from this repo in your target project.

## Prerequisites
- VS Code with GitHub Copilot Chat enabled
- Optional: MCP servers for SequentialThinking, Memory, and GitHub

## Setup Steps
1) **Copy the folder** from the source repo:
   ```bash
   cp -r /path/to/pdd/dot_github ./.github
   ```

2) **Commit the files** in your repo:
   - `.github/chatmodes/*` (all design thinking chatmodes)
   - `.github/prompts/*` (execute and document prompts)
   - `.github/copilot-instructions.md` (chatmode-first instructions)

3) **Reload VS Code**, open Copilot Chat, and switch to design thinking chatmodes:
   - `Ideate`, `Plan`, `Execute`, `Document` for design thinking workflow
   - `Concise` for quick tasks, `Research` for information gathering

4) **Test design thinking workflow** and validate outputs:
   - **Ideate chatmode** → `ideate/YYYY-MM-DD-<slug>.md`
   - **Plan chatmode** → `plan/YYYY-MM-DD-<slug>-plan.md`
   - **Execute chatmode** → `execute/T-XXX-<slug>/README.md`
   - **Document chatmode** → `execute/brainstorm-dev-session-YYYY-MM-DD.md`

5) **Customize for your project**:
   - Update quality gates (build/lint/test commands) in `.github/copilot-instructions.md`
   - Adjust artifact folder structure if needed

## Design Thinking Workflow
1. **Ideate**: User-centered problem exploration and solution concepts
2. **Plan**: Convert concepts into learning experiments and testable prototypes
3. **Execute**: Run experiments, build prototypes, validate assumptions
4. **Document**: Synthesize learnings and prepare for next iteration

## Conventions
- Slugs: kebab‑case; Task IDs: zero‑padded (`T-001`); Dates: ISO
- One primary artifact per chatmode run; link related artifacts
- Focus on learning validation over feature completion

## Troubleshooting
- **Chatmodes not available?**
  - Ensure the folder is named `.github/` at the repository root and reload VS Code
- **Artifacts not created under the right folders?**
  - Confirm the chatmodes reference the correct relative paths and your repo allows writing to them
- **Need to adapt commands?**
  - Replace validation/build/lint steps in `.github/copilot-instructions.md` with your project's actual commands
- **Design thinking workflow unclear?**
  - Start with Ideate chatmode to explore user problems before jumping to solutions