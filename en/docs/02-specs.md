# 2) Specs (e.g., React + TypeScript + Vite)

> ⚠️ The content in this document is an example. Replace it with your actual project details.

This document defines the technical specifications and operational rules for implementation.  
(Pin versions to match your team conventions or template standards.)

---

## A. Runtime / Core

- **Framework**: React 19
- **Language**: TypeScript 5.x (strict mode)
- **Build Tool**: Vite 6
- **Routing**: React Router v7
- **Package Manager**: pnpm

---

## B. Data Fetching / Server State

### TanStack Query (React Query)
- Purpose: Server state caching/synchronization, standardized loading/error handling

#### Recommended Rules
- Design cache keys by domain (e.g., `['tasks', taskId]`, `['users', 'me']`)
- Unify invalidation strategy on mutation success
- Set staleTime per domain (frequently changing data: 0, rarely changing data: 5 min)

---

## C. Client State (Global UI State)

### Zustand
- Purpose: Manage client-side UI state globally

#### Recommended Rules
- Do not store server data in Zustand (server state is TanStack Query's responsibility)
- Use persist middleware only for user preferences (theme, language, etc.)

---

## D. API Layer & Other Specs

- API communication: Axios (interceptors for automatic auth token injection)
- Styling: Tailwind CSS v4

#### Rules (Important)
- API calls must go through the `shared/api` wrapper only (direct axios.get is forbidden)
- Design tokens must be defined in the Tailwind config; hard-coded colors/spacing are forbidden
