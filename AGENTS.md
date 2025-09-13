# AGENTS.md

## Project overview
This repository develops Prompt-Driven Development (PDD) chat modes and prompts for reuse in other projects. **Do NOT activate the chat modes or prompts in this repository** - they are authoring sources only.

## Repository purpose
- Author and iterate chat modes in `dot_github/chatmodes/`
- Author phase prompts in `dot_github/prompts/`
- Provide examples and templates for downstream adoption
- Keep `dot_github/` folder intact (do not rename to `.github/` here)

## Development workflow
- Edit prompts and chat modes under `dot_github/`
- Test changes by copying `dot_github/` to a separate sandbox repo and renaming to `.github/`
- Keep examples minimal with concrete file paths
- Follow naming conventions: kebab-case slugs, zero-padded tasks (`T-001`), ISO dates

## File structure
- `dot_github/chatmodes/` - Concise, Plan, Research chat modes (authoring source)
- `dot_github/prompts/` - Ideate, Plan, Execute, Document phase prompts (authoring source)
- `dot_github/copilot-instructions.md` - Template instructions for consumer repos
- `.github/copilot-instructions.md` - Active instructions for this repo (canonical)
- `ideate/`, `plan/`, `execute/` - Example artifact folders (not activated here)
- `templates/COPYRIGHT_HEADER.txt` - Attribution header template

## Testing instructions
1. Copy `dot_github/` to a test repository: `cp -r dot_github /path/to/test-repo/.github`
2. In the test repo, commit `.github/chatmodes/*`, `.github/prompts/*`, `.github/copilot-instructions.md`
3. Open VS Code with Copilot Chat and switch between modes to validate behavior
4. Run phase prompts and verify artifacts are created in expected locations

## Code style and conventions
- Use kebab-case for slugs in filenames
- Zero-pad task IDs: `T-001`, `T-002`, etc.
- ISO date format: `YYYY-MM-DD`
- One primary artifact per phase run
- Link related artifacts in outputs
- Include concrete file paths in guidance text

## Consumer integration
Downstream repositories should:
1. Copy `dot_github/` to their repo and rename to `.github/`
2. Adjust quality gates in `.github/copilot-instructions.md` to their build/lint/test commands
3. See `dot_github/CONSUMER_SETUP.md` for detailed checklist

## Attribution requirements
- This repo is CC BY 4.0 licensed
- Include attribution as described in `CONTRIBUTING.md`
- Use `templates/COPYRIGHT_HEADER.txt` when adding files that should carry headers

## Security considerations
- No build system or runtime dependencies in this repo
- All content is documentation and templates
- Validate any executable content when adopting in consumer repositories

## What NOT to do
- Do not rename `dot_github/` to `.github/` in this repository
- Do not activate or use the PDD workflow in this repository
- Do not create actual ideate/plan/execute artifacts here (examples only)
- Do not modify `.github/copilot-instructions.md` to enable the workflow here
