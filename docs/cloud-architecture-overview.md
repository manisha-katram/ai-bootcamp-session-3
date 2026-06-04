# Cloud Architecture Overview

This monorepo contains a React frontend and a Node.js backend managed from a single workspace. The frontend is the user-facing application, and it communicates with the backend over HTTP for task operations.

```mermaid
flowchart LR
    U[User]
    FE[Frontend\nReact app\npackages/frontend]
    BE[Backend\nExpress API\npackages/backend]
    DB[(Task Data\nSQLite storage)]
    WS[Monorepo Workspace\nRoot package.json\nNPM workspaces]

    U --> FE
    FE -->|HTTP /api/tasks| BE
    BE --> DB
    WS -. manages .-> FE
    WS -. manages .-> BE
```

## Create TODO Sequence

```mermaid
sequenceDiagram
    actor User
    participant Frontend as React Frontend
    participant Backend as Express API
    participant Database as SQLite Task Store

    User->>Frontend: Enter task details and submit form
    Frontend->>Backend: POST /api/tasks
    Backend->>Backend: Validate title and request payload
    Backend->>Database: Insert new task
    Database-->>Backend: Return saved task record
    Backend-->>Frontend: 201 Created with task data
    Frontend-->>User: Show updated task list
```

## Components

- Frontend: React application in `packages/frontend`
- Backend: Express API in `packages/backend`
- Data store: SQLite-backed task storage owned by the backend
- Monorepo orchestration: root workspace scripts in `package.json`