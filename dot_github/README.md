# PDD Chat Modes & Prompts — Dev Source

This folder contains the authoring sources for PDD chat modes and prompts. Do NOT rename `dot_github/` to `.github/` in this repository; activation should happen in a downstream repo or sandbox.

What belongs here
- `chatmodes/` — author and iterate chat modes (Concise, Plan, Research)
- `prompts/` — author phase prompts (ideate, plan, execute, document)
- Keep examples minimal; include concrete file paths in the guidance you write

Authoring guidance
- Make small, focused changes per PR; describe intent and include example invocations
- Reference exact artifact paths: `ideate/YYYY-MM-DD-<slug>.md`, `plan/YYYY-MM-DD-<slug>-plan.md`, `execute/T-XXX-<slug>/README.md`
- Follow naming conventions: kebab-case slugs, zero-padded tasks (`T-001`), ISO dates
- Attribution: if adding files that should carry a header, use `templates/COPYRIGHT_HEADER.txt`

Testing changes (in a separate repo)
1) Copy `dot_github/` into a sandbox repo and rename to `.github/`
2) Commit `.github/chatmodes/*`, `.github/prompts/*`, `.github/copilot-instructions.md` (if not present, copy from this repo)
3) In VS Code with Copilot Chat, switch modes and run the prompts; adjust per feedback

Consumer integration
- See `dot_github/CONSUMER_SETUP.md` for a concise checklist to enable these assets in another repository.
