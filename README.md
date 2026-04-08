[한국어](README.ko.md)

# Austin's Docs Architecture for AI

A docs-first repository template for teams that want AI coding agents and humans to work from the same source of truth.

Instead of rebuilding context in every prompt, this repository keeps project rules, architecture, product scope, TODOs, and work history in a fixed document structure inside the repo. In this model, the docs act as the project's single source of truth: the first place an agent or developer should check before making changes. Agents read those files before acting, then implement changes and leave durable follow-up context.

## What It Solves

- project context disappearing into chat history
- repeated onboarding for every new agent session
- architecture, specs, and product scope drifting away from the codebase
- scattered TODOs and weak handoff between contributors

## Core Pieces

- `AGENTS.md`
  - shared working agreement for any agent
  - defines required reading, checklists, and change rules
- `docs/01-folder-architecture.md`
  - defines repository structure and folder responsibilities
- `docs/02-specs.md`
  - defines stack choices, implementation rules, and constraints
- `docs/03-product-plan.md`
  - defines product scope, users, and core features
- `docs/reports/`
  - stores completed work notes and major change records
- `docs/todo/`
  - stores blocked or deferred follow-up work

## Repository Structure

```text
.
├─ README.md          # English
├─ README.ko.md       # 한국어
├─ LICENSE
├─ en                 # ← English template bundle
│  ├─ AGENTS.md
│  └─ docs
│     ├─ 01-folder-architecture.md
│     ├─ 02-specs.md
│     ├─ 03-product-plan.md
│     ├─ reports
│     │  └─ _template.md
│     └─ todo
│        ├─ 00-todo-list.md
│        └─ _template.md
└─ ko                 # ← 한국어 템플릿 번들
   ├─ AGENTS.md
   └─ docs
      ├─ 01-folder-architecture.md
      ├─ 02-specs.md
      ├─ 03-product-plan.md
      ├─ reports
      │  └─ _template.md
      └─ todo
         ├─ 00-todo-list.md
         └─ _template.md
```

Each language folder (`en/`, `ko/`) contains a complete template bundle: `AGENTS.md` + `docs/`.

## How It Works

1. Fill in `AGENTS.md` and `docs/01`, `docs/02`, `docs/03` with your team rules and project context.
2. Have agents read those files and `docs/todo/00-todo-list.md` before starting work.
3. If implementation and docs diverge, update the docs first.
4. Record important work in `docs/reports/` and deferred work in `docs/todo/`.

## Recommended Use Cases

- teams starting a new project and wanting clear AI collaboration rules from day one
- repositories where multiple agents and developers work interchangeably
- projects that want architecture, specs, and work memory versioned alongside code
- individuals experimenting with docs-driven AI development workflows

## Getting Started

> **The easiest way:** Just tell your AI agent:  
> *"Apply https://github.com/EunHyeokJung/austin-docs-architecture to this workspace."*  
> The AI will handle everything below automatically.

### AI Setup Instructions (for agents)

If you are an AI agent asked to apply this template to a project, follow these steps **in order**:

**Step 1 — Choose language**
- Ask the user which language they prefer: **English (`en/`)** or **Korean (`ko/`)**.
- If the user doesn't specify, infer from the project's existing files or conversation language.

**Step 2 — Copy the template bundle to the project root**
- Copy `AGENTS.md` and `docs/` from the chosen language folder to the project root:

```bash
# English
cp en/AGENTS.md . && cp -r en/docs . && rm -rf en ko

# Korean
cp ko/AGENTS.md . && cp -r ko/docs . && rm -rf en ko
```

**Step 3 — Understand the project**
- Read the project's existing codebase: package.json, folder structure, source files, configs, etc.
- If the project is empty or has no code yet, ask the user the following:
  1. What is the core purpose, key features, and target users of the service?
  2. What tech stack will be used? (framework, language, state management, styling, etc.)
  3. Any preferred folder structure, architecture pattern, or coding conventions?

**Step 4 — Fill in the documents**
- Replace all example/placeholder content in these files with the actual project information:
  - `AGENTS.md` — update checklists, code rules, and references to match the project
  - `docs/01-folder-architecture.md` — define the real folder structure and responsibilities
  - `docs/02-specs.md` — define the actual tech stack, libraries, and implementation rules
  - `docs/03-product-plan.md` — define the real product scope, users, and features
- Remove the `⚠️ example` warnings from each document.

**Step 5 — Clean up**
- Delete the initialization comment block at the top of `AGENTS.md` (the `<!-- ... -->` block).
- Optionally remove `README.md` and `README.ko.md` if they are from this template repo (the project should have its own README).

**After setup, the project should look like:**

```text
.
├─ AGENTS.md
├─ docs
│  ├─ 01-folder-architecture.md
│  ├─ 02-specs.md
│  ├─ 03-product-plan.md
│  ├─ reports
│  │  └─ _template.md
│  └─ todo
│     ├─ 00-todo-list.md
│     └─ _template.md
└─ (project files...)
```

### Manual Setup

If you prefer to set it up yourself:

1. Clone or copy this repository into your project.
2. Pick your language and copy the bundle to the project root:

```bash
# English
cp en/AGENTS.md . && cp -r en/docs . && rm -rf en ko

# Korean
cp ko/AGENTS.md . && cp -r ko/docs . && rm -rf en ko
```

3. Replace the example content in `AGENTS.md`, `docs/01`, `docs/02`, `docs/03` with your project details.
4. Delete the initialization comment block at the top of `AGENTS.md`.
5. Keep work records in `docs/reports/` and deferred tasks in `docs/todo/`.

## Intended Workflow

<img width="960" height="540" alt="agent workflow chart" src="https://github.com/user-attachments/assets/d9f95731-e6d6-4e9f-aed6-90a511294c80" />


## Operating Principles

- docs are execution context, not passive reference material
- docs should remain the project's single source of truth
- when docs and code disagree, align the docs before implementation
- TODOs should have a single discoverable index
- work history should help the next person and the next session

## License

This repository uses a custom template license.

- You may use and modify it in your own projects.
- You may use it in commercial products or client work.
- You may not sell or redistribute this structure itself as a template, starter, or boilerplate product.

See [LICENSE](LICENSE) for full terms.
