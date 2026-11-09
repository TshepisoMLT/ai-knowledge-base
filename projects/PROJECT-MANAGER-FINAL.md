# project-manager-final — Project Context

**Source repository:** [TshepisoMLT/project-manager-final](https://github.com/TshepisoMLT/project-manager-final)  
**Branch inspected:** `main`  
**Inspected:** 2026-11-09  
**Repository status:** public, not archived

## What it is

A project/task manager aimed at freelancers and small teams. The current visible product is a browser-local prototype with a dashboard, project management, a Kanban board, task detail workflows, project templates, search, and local reminders.

The repository also contains an API specification, generated API client/Zod packages, and an Express server workspace. Do not mistake those scaffolds for a working multi-user backend: the registered server routes and database schema inspected here are still minimal.

## Workspace and stack

This is a pnpm monorepo with workspaces under `artifacts/*`, `lib/*`, and `scripts`.

- Root stack: Node.js 24, TypeScript 5.9, pnpm workspaces.
- Frontend: React, Vite, TypeScript, Wouter routing, Tailwind CSS 4, Lucide icons.
- API server scaffold: Express 5, CORS, Pino logging.
- Contract/codegen packages: OpenAPI 3.1, Orval-generated React client and Zod types.
- Database package: Drizzle ORM dependency and configuration scaffold.

## Workspace map

| Path | Role |
|---|---|
| `artifacts/project-manager/` | Actual project-manager web app |
| `artifacts/api-server/` | Express server scaffold |
| `artifacts/mockup-sandbox/` | Separate UI mockup sandbox |
| `lib/api-spec/` | OpenAPI source contract and Orval config |
| `lib/api-client-react/` | Generated React API client and custom fetch utility |
| `lib/api-zod/` | Generated schemas/types from the API contract |
| `lib/db/` | Drizzle DB package; schema index currently placeholder |
| `scripts/` | Workspace scripts |

## Implemented UI and data behavior

The frontend entry component is `artifacts/project-manager/src/App.tsx`. It wires a `DataProvider` to Wouter routes:

- `/` and `/dashboard` — overview dashboard
- `/projects` — project list, templates, active/archived views
- `/projects/:projectId` — project board and task details
- `/search` — cross-project/task search

The UI supports project create/edit/archive/restore, task create/edit/delete, task status moves, priorities, assignees, due dates, checklist items, comments, activity history, templates, filters/sort, and local reminder center.

The store is `artifacts/project-manager/src/store.tsx`. It:

- seeds sample projects, tasks, templates, and reminders;
- reads/writes the `fieldnotes.project-manager.v1` key in browser `localStorage`;
- maintains task/project/template/reminder state in the React app;
- does not call the generated API client for current persistence.

Thus the current persistence boundary is the browser profile and origin. Different browsers/devices/users do not share changes. Clearing site data can remove the local copy.

## API/backend scaffold versus live implementation

### API contract

`lib/api-spec/openapi.yaml` defines a broad Project Manager API contract. Its areas include health, workspace, projects/tasks, workload, planning (milestones, labels, saved views, templates), collaboration (notifications, invitations, client reviews/approvals), storage/attachments, and calendar sync/export.

### Registered server routes

The API app mounts `/api`. The route index imports only `health.ts`, and that file registers `GET /healthz`. The inspected route tree contains only the index and health route.

### Database schema

`lib/db/src/schema/index.ts` contains commented example code and `export {}`; no Drizzle tables are defined there at this snapshot.

### Generated clients

`lib/api-client-react` and `lib/api-zod` contain generated/schema-derived code. Those artifacts can reflect the OpenAPI contract even when the backend route or database implementation does not exist yet.

**AI rule:** before wiring a new frontend feature to the API, verify the server route, handler, validation, authorization, database schema/migration, client generation, and tests. Keep the local prototype's limitation explicit until the full path is implemented.

## Run and validate

From the workspace root:

```bash
pnpm install
pnpm --filter @workspace/project-manager run dev
pnpm --filter @workspace/project-manager run typecheck
pnpm --filter @workspace/project-manager run build
```

Root scripts include `pnpm run typecheck` and `pnpm run build`. The server package has its own `dev`, `build`, `start`, and `typecheck` scripts; it requires `PORT` at startup.

Publishing notes in the project docs refer to Replit's Publish action. No external service/environment variable is required for the browser-local frontend prototype.

## Important configuration and safety notes

- `pnpm-workspace.yaml` enforces `minimumReleaseAge: 1440` (one day) and defines trusted exclusions. Preserve this supply-chain policy; do not casually disable it.
- Root workspace packages and generated files should be changed through their source configs/specs and regeneration workflow where applicable.
- Do not store secrets or business-critical records in the current localStorage-only app.
- Authentication, user/team roles, server-side ownership checks, cross-device sync, email/push reminders, and shared persistence are explicitly not implemented in the product context docs.
- The UI's local reminders are not messages sent to another person.

## Key source links

- [Root Replit operating guide](https://github.com/TshepisoMLT/project-manager-final/blob/main/replit.md)
- [Frontend README](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/project-manager/README.md)
- [Project context](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/project-manager/PROJECT_CONTEXT.md)
- [Architecture](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/project-manager/docs/ARCHITECTURE.md)
- [Deployment](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/project-manager/docs/DEPLOYMENT.md)
- [Frontend App](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/project-manager/src/App.tsx)
- [Frontend store](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/project-manager/src/store.tsx)
- [OpenAPI contract](https://github.com/TshepisoMLT/project-manager-final/blob/main/lib/api-spec/openapi.yaml)
- [Express route index](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/api-server/src/routes/index.ts)
- [Health route](https://github.com/TshepisoMLT/project-manager-final/blob/main/artifacts/api-server/src/routes/health.ts)
- [Drizzle schema index](https://github.com/TshepisoMLT/project-manager-final/blob/main/lib/db/src/schema/index.ts)

## AI quick-start prompt

> Read `replit.md`, the frontend `README.md`, `PROJECT_CONTEXT.md`, `docs/ARCHITECTURE.md`, and the relevant source files. The frontend currently persists to browser `localStorage`. The OpenAPI spec is broader than the mounted Express routes, and the DB schema is a placeholder. Keep those boundaries accurate; do not claim cloud persistence or multi-user behavior unless you implement and verify the complete backend path.
