# Copilot Instructions — Design Thinking PDD

Operate with Design Thinking Prompt‑Driven Development (PDD) and MCP-first behavior. Use chatmodes for human-in-the-loop design thinking sessions: **Ideate → Plan → Execute → Document**. For small, rapid tasks, switch to the Concise chat mode.

## Design Thinking Chatmodes
- **Ideate**: Switch to design thinking ideation for user-centered problem exploration and solution concepts
- **Plan**: Switch to prototyping-focused planning for learning experiments and assumption testing
- **Execute**: Switch to experimentation mode for rapid prototyping and validation
- **Document**: Switch to learning synthesis for capturing insights across brainstorm-dev sessions
- **Concise**: Switch for ≤ 10 lines; next action first; surgical changes; executing single plan tasks
- **Research**: Switch for citations + synthesis → actionable steps; read-first, no code edits

## Design Thinking Workflow
1. **Ideate**: Human-centered exploration of user problems and solution concepts
2. **Plan**: Convert concepts into testable prototypes and learning experiments
3. **Execute**: Run experiments, build prototypes, validate assumptions
4. **Document**: Synthesize learnings and prepare for next iteration

## Global Behavior
- MCP‑first: use SequentialThinking, Memory (persist decisions + artifact paths), and GitHub (issues/PRs/repo context)
- Traceability: state assumptions, decisions, and exact file paths in outputs
- Safety: if a request is harmful/forbidden → "Sorry, I can't assist with that."
- Persistent progress: Use Memory MCP to maintain context across design thinking sessions

## Artifact Structure
Design thinking chatmodes produce these artifacts:
- **Ideate** → `ideate/YYYY-MM-DD-<slug>.md` (user-centered concepts and solution exploration)
- **Plan** → `plan/YYYY-MM-DD-<slug>-plan.md` (learning experiments and assumption testing)
- **Execute** → `execute/T-XXX-<slug>/README.md` (experiment results and prototype outcomes)
- **Document** → `execute/brainstorm-dev-session-YYYY-MM-DD.md` (session learning synthesis)

Additional prompts for structured tasks:
- Execute: `.github/prompts/execute.prompt.md` → structured task execution
- Document: `.github/prompts/document.prompt.md` → comprehensive documentation summaries

## File/Folder Conventions
- Use kebab-case `<slug>`, zero-padded task ids (`T-001`), ISO dates
- One primary artifact per phase run; link related artifacts
- Experiments focus on learning validation over feature completion
- Plans include assumption testing and pivot triggers

## Execution Rules for Experiments
- Choose experiments based on riskiest assumptions first
- Each task: learning objective, hypothesis, success criteria, pivot triggers
- Quality gates: build, lint/typecheck, unit tests, smoke test (adjust to project)
- Update plans with learning outcomes and strategic recommendations

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
- Design thinking ideation: "Switch to Ideate and explore user needs for <problem>"
- Prototyping planning: "Switch to Plan and convert ideation into learning experiments"
- Rapid experimentation: "Switch to Execute and run the next prototype experiment"
- Learning synthesis: "Switch to Document and synthesize session insights"
- Concise execution: "Switch to Concise and execute the next eligible plan task"
- Research mode: "Switch to Research and summarize options with citations"
