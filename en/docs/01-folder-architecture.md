# 1) Folder Architecture (e.g., React SPA + FSD)

> ⚠️ The content in this document is an example. Replace it with your actual project details.

This document defines the frontend folder architecture for the **TaskFlow** service.  
Core goals:

- Separate service app layers
- Structure components using FSD (Feature-Sliced Design)
- Separate state management responsibilities (server state vs. UI state)

---

## A. Top-Level Structure (Recommended)

```txt
root
├─ .github
│  ├─ workflows
│  └─ ISSUE_TEMPLATE
├─ apps
│  ├─ web                                # Main web app
│  └─ admin                              # Admin web app (to be added later)
│
├─ packages                              # (for monorepo setups)
│  ├─ ui                                 # Shared UI components
│  └─ utils                              # Shared utilities
│
├─ docs                                  # ✅ AI agent context folder
│  ├─ 01-folder-architecture.md
│  ├─ 02-specs.md
│  ├─ 03-product-plan.md
│  ├─ reports
│  │  └─ _template.md
│  └─ todo
│     ├─ _template.md
│     └─ 00-todo-list.md
│
├─ package.json
└─ tsconfig.json
```

> `docs/reports` is for recording completed or noteworthy work history.  
> `docs/todo` is for deferred work that is blocked by prerequisites, API integration, policy decisions, etc.

---

## B. Internal Structure (e.g., FSD Style)

The internal structure follows **FSD (Feature-Sliced Design)**:

```txt
apps/web/src
├─ app                               # Application entry point and global config
│  ├─ providers                      
│  ├─ router                         
│  └─ styles                         
│
├─ pages                             # Route-level page components
│  ├─ dashboard
│  └─ settings
│
├─ widgets                           # Reusable, self-contained view blocks
│  ├─ task-board
│  └─ sidebar
│
├─ features                          # Core feature units with business logic
│  └─ create-task
│
├─ entities                          # Domain models and domain logic
│  └─ task
│
└─ shared                            # Global shared modules (UI, API, etc.)
   ├─ api
   ├─ ui
   └─ lib
```

- Upper layers may only import from lower layers (e.g., features → entities ✅, entities → features ❌)
- shared can be imported from any layer
- Direct imports between slices in the same layer are forbidden
