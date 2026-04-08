# 3) Product Plan (e.g., TaskFlow)

> ⚠️ The content in this document is an example. Replace it with your actual project details.

This document outlines the product plan (requirements, user flows, feature scope) for the "TaskFlow" service.  
The current target is **MVP Phase 1**.

---

## A. Service Overview

### Purpose
- Centralize task management and progress tracking for small teams
- Provide intuitive kanban-board-based task management

### Target Users
- Startup / small team leaders
  - Want to see each member's workload at a glance
- Developers / designers (team members)
  - Want to quickly check their tasks and update status

---

## B. Service Composition (Apps)

### 1) User-Facing Web
- Dashboard (kanban board + list view)
- Task create / edit / delete
- Team member invitations and permission management

### 2) Admin Web (future)
- Project-wide analytics dashboard
- Team / member management

---

## C. Page Structure (Core Routes)

### Dashboard (/dashboard)
- Kanban board: To Do / In Progress / Done columns
- Drag-and-drop task cards
- Filters: assignee, priority, due date

### Task Detail (/tasks/:id)
- Task title, description, attachments
- Comments / activity log
- Status changes, assignee assignment

---

## D. Core Feature Requirements (MVP Focus)

### 1) Task CRUD
- Title, description, priority (Low/Medium/High), and due date are required
- Drag-and-drop to change task status

### 2) Authentication & Team Management
- Email / social login (Google, GitHub)
- Create a team, then add members via invite link
