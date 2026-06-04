# Product Requirements Document (PRD) - TODO App Upgrade

## 1. Overview

We are upgrading the basic TODO app (currently supporting only `title` and `completed`) to support due dates, priority levels, and task filters so users can better organize and prioritize their work. The goal is a simple, teachable enhancement with no backend changes — all data remains in local storage.

---

## 2. MVP Scope

- **Due Date field** — each task may optionally include a `dueDate` in ISO `YYYY-MM-DD` format; invalid values are ignored and treated as absent
- **Priority field** — each task includes a `priority` enum (`P1 | P2 | P3`), defaulting to `P3`
- **Filter tabs** — three views: **All**, **Today**, **Overdue**
  - **All**: shows all tasks, both complete and incomplete
  - **Today**: shows only incomplete tasks due today
  - **Overdue**: shows only incomplete tasks with a past due date
- **Data validation**
  - `title`: required
  - `priority`: must be `"P1"`, `"P2"`, or `"P3"`; defaults to `"P3"`
  - `dueDate`: optional; invalid values treated as absent
- **Local storage only** — no backend or external storage changes

---

## 3. Post-MVP Scope

- **Visual overdue highlighting** — overdue tasks are highlighted in red so they stand out
- **Color-coded priority badges** — red badge for P1, orange for P2, gray for P3
- **Sorting rules** — tasks sorted automatically: overdue first → priority ascending (P1 → P3) → due date ascending → undated tasks last

---

## 4. Out of Scope

- Notifications / reminders
- Recurring tasks
- Multi-user support
- Keyboard navigation and accessibility features
- External or backend storage (local storage only)
