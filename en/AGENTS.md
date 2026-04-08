<!-- 
[AI Agent Initialization Guide]
If this file and the docs/ files still contain example/placeholder content, follow these steps:

1. Read the project's existing codebase (package.json, folder structure, source files, configs, etc.).
2. If the project is empty or lacks sufficient context, ask the user:
   - What is the core purpose, key features, and target users of the service?
   - What tech stack will be used? (framework, language, state management, styling, etc.)
   - Any preferred folder structure, architecture pattern, or coding conventions?
3. Based on what you learn, replace the example content in these files with actual project information:
   - `AGENTS.md` — update checklists, code rules, and references
   - `docs/01-folder-architecture.md` — define the real folder structure and responsibilities
   - `docs/02-specs.md` — define the actual tech stack, libraries, and implementation rules
   - `docs/03-product-plan.md` — define the real product scope, users, and features
4. Remove the `⚠️ example` warnings from each document.
5. Once all documents are filled in, delete this entire comment block (from line 1 to here).
-->

# Agent Working Agreement

This file is for any developer agent (Codex, Copilot, etc.) working in this repo.
The goal is to keep everyone aligned even when different agents are used.

## Required Reading (Before Every Task)
- `docs/01-folder-architecture.md`
- `docs/02-specs.md`
- `docs/03-product-plan.md`
- `docs/todo/00-todo-list.md`

## Pre-Task Checklist
- Have I read the required documents above?
- Have I checked `docs/todo/00-todo-list.md`?
- Does this task stay within [project goals / scope]?
- Does it follow the folder structure and [architecture pattern] rules?
- Are API calls limited to [allowed API paths / rules]?
- Does the UI/styling follow [project styling rules]?
- If a related TODO exists, have I read the relevant `docs/todo/*.md` and informed the user first?

## Code Change Rules (Summary)
- [Example: Do not import generated code directly]
- [Example: Prefer shared/ui components]
- [Example: Server state via TanStack Query, UI state via Zustand]
- [Add your own project conventions here]

## Documentation Update Rules
- When architecture/specs/plans change, update the corresponding document (01/02/03)
- If the current task contradicts a document, update the document first, then change the code
- Record significant changes in `docs/reports` using the format `yymmdd-HHMM-NN-task-keyword.md`
- Template: `docs/reports/_template.md`
- If a task cannot be completed now but must be done later, add a TODO document in `docs/todo`
- When adding a TODO, also add a one-line summary to `docs/todo/00-todo-list.md`
- When a TODO is completed, delete the TODO file, write a work record in `docs/reports/`, and remove it from `docs/todo/00-todo-list.md`
- When receiving a TODO-related request, check `docs/todo/00-todo-list.md` first; if a related item exists, read the TODO document and inform the user about its existence and scope before proceeding

## Notes
- Keep this document concise — it is for agents only
- Rules may be added here, but if they conflict with 01/02/03, those documents take precedence
