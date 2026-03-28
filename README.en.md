[한국어](README.md) | [English](README.en.md)

# Austin's Docs Architecture for AI

Docs-first repository scaffolding for AI-assisted software development.

This project treats documentation as operational memory for coding agents and human collaborators. Instead of relying on a long prompt or a fresh explanation every session, the repository keeps project rules, architecture, product context, TODOs, and work history in predictable files that an agent can read before acting.

## Core Ideas

### 1. Documents as Memory
Project context should live in the repository, not only in chat history.

- `AGENTS.md` defines the working agreement for any agent.
- `docs/01-folder-architecture.md` defines repository and source structure.
- `docs/02-specs.md` defines stack, runtime rules, and implementation constraints.
- `docs/03-product-plan.md` defines product scope, roadmap, and domain intent.
- `docs/reports/` stores work history for handoff and traceability.
- `docs/todos/` stores blocked or postponed work for later.

### 2. Pre-flight Check
Before changing code, the agent should read the minimum required context and verify that the task fits the project's structure, scope, and rules.

This repository encodes that behavior in `AGENTS.md`:

- read the foundation docs first
- check the central TODO list
- confirm the task fits the project scope
- update docs first if code and docs diverge
- leave follow-up memory in `reports` or `todos`

### 3. Working Agreement
The repository provides a stable contract between different agents and developers.

That means:

- less prompt rebuilding
- fewer hallucinated assumptions
- better handoff between sessions
- clearer boundaries for architecture and product decisions

## Repository Structure

The current repository is intentionally small and focused on the documentation contract itself.

```text
.
├─ AGENTS.md
└─ docs
   ├─ 01-folder-architecture.md
   ├─ 02-specs.md
   ├─ 03-product-plan.md
   ├─ reports
   │  └─ _template.md
   └─ todos
      ├─ 00-todo-list.md
      └─ _template.md
```

## What Each File Does

### `AGENTS.md`
The entry point for any coding agent.

It defines:

- what must be read before work starts
- the pre-flight checklist
- summary coding rules
- when docs must be updated
- how work history and TODOs should be recorded

### `docs/01-folder-architecture.md`
The structural source of truth.

Use it to document:

- top-level repository layout
- app and package boundaries
- architectural pattern choices
- folder responsibilities

### `docs/02-specs.md`
The implementation contract.

Use it to document:

- framework and runtime choices
- data fetching rules
- state management rules
- API usage conventions
- styling constraints

### `docs/03-product-plan.md`
The product boundary.

Use it to document:

- service purpose
- target users
- MVP scope
- route and page plan
- core feature requirements

### `docs/reports/`
The handoff memory.

Use reports when work is completed, significant, or needs a durable record.

Typical use cases:

- feature implementation summary
- refactor history
- risk notes for the next agent
- important decision trail

### `docs/todos/`
The deferred work queue.

Use TODO docs when work cannot be completed yet because of blockers such as:

- missing API contracts
- unresolved policy decisions
- dependency on another task
- timing constraints

`docs/todos/00-todo-list.md` acts as the index that agents should check first.

## Why This Helps

### A Better Base Prompt
The repository itself becomes the base prompt.

Agents can ground their work in persisted constraints, product context, and architecture rules instead of inferring them from incomplete code or a short instruction.

### Task Routing
The workflow pushes the agent to think like a peer developer:

1. read the context
2. align docs if needed
3. implement
4. leave memory for the next handoff

That makes planning, design, and implementation part of one continuous loop.

### Automatic Context Relay
An agent does not need to read the whole codebase first.

With a stable document contract, it can bootstrap from a small set of files, then expand only into the code or TODOs relevant to the task. This reduces context cost and improves continuity across new sessions.

## Intended Workflow

<img width="1118" height="629" alt="austin-docs-architecture-workflow-chart" src="https://github.com/user-attachments/assets/88357f8c-0772-4eac-b5be-e600c197f988" />

## Current State of This Repo

This repository is currently a starter template for the documentation architecture itself.

- The foundation docs still contain placeholder sections.
- `AGENTS.md` also still contains template placeholders.
- The repository already demonstrates the intended file contract and report/TODO templates.
- There is a path naming mismatch in the current files: some instructions reference `docs/todo`, while the actual directory in this repository is `docs/todos`.

That makes this repository useful both as:

- a reusable starter for new projects
- a reference example for docs-driven AI collaboration

## How To Use This Template

1. Copy this repository into a new project.
2. Replace the placeholder content in `AGENTS.md` and `docs/01`, `docs/02`, `docs/03`.
3. Align the folder naming convention for `todo` vs `todos`.
4. Keep the docs updated whenever architecture, specs, or product scope change.
5. Record notable work in `docs/reports/`.
6. Record blocked follow-up work in `docs/todos/`.

## Notes

- The current document templates are written in Korean.
- This repository is not an application runtime; it is a collaboration structure for applications.

## License

This repository uses a custom template license.

- You may use and modify it in your own projects.
- You may use it in commercial products or client work.
- You may not sell or redistribute this structure itself as a template, starter, or boilerplate product.

See [LICENSE](LICENSE) for the full terms.
